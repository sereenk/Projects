# GET YOUR OWN SPOTIFY WRAPPED WITH SOME MORE DETAILED ANALYSIS OF YOUR MUSICAL INCLINATIONS!

# ABOUT 

This is my final project for an Intermediate Python Programming class(SI 507) at the University of Michigan, Ann Arbor. A couple of days ago, I saw my Spotify wrapped and that made me so excited! However, I wanted to see some more information on my musical inclinations. So I wondered, what if I try making it for my top artist tracks? So, I decided to do a project using Spotify's API and the iTunes API. I accessed the API, retrieved my information, processed it to create a data frame and then create some visualizations. I wanted to make it interactive, so that non-Spotify users can use this as well. So I added in an iTunes option for users to search a particular term within the iTunes API so they can see its respective songs, books, and other related information!![image](https://user-images.githubusercontent.com/59630489/146658262-4cff0ab5-4e2d-4e4f-a286-499d0a630988.png)


## DATA SOURCES : 

### 1. SPOTIFY API 
The first data source is the Spotify API. The Spotify API gives developers a way to access their data on artists, tracks, playlists and users through their web API. This API will be used to extract relevant data and used to analyze a users' musical inclinations.
Here is some more information on the API - https://developer.spotify.com/documentation/web-api/
![image](https://user-images.githubusercontent.com/59630489/146658286-1751b120-a3b7-4a15-8c75-901caf539158.png)

### 2. I-TUNES API :

The second source was the ITUNES API. The data will be retrieved from this API depending upon what the user searches. The data will then be processed and stored  as lists and information will be finally returned to the user. The iTunes API doesn't need any authorization so it can be easily accessed. 

Here is some more information on the API - https://affiliate.itunes.apple.com/resources/documentation/itunes-store-web-service-search-api/
![image](https://user-images.githubusercontent.com/59630489/146658290-446e78d1-58c7-4bed-89ca-05216c78f239.png)

# SETUP

### Accessing the spotify API:

STEP 1: Step 1: Log in or create an account 
STEP 2: Go to the dashboard page for Spotify Developers (https://developer.spotify.com/dashboard/login).
STEP 3: 'Create an App' :  To do so, go to your Dashboard and click on the Create an App button to open the following dialog box:

<img width="302" alt="Screen Shot 2021-12-18 at 2 49 47 PM" src="https://user-images.githubusercontent.com/59630489/146657534-e35fb1b7-e1ad-41a2-9e81-04c114423b09.png">

STEP 4: Enter an App Name and App Description of your choice (they will be displayed to the user on the grant screen), put a tick in the Developer Terms of Service checkbox and finally click on CREATE. Your application is now registered, and you’ll be redirected to the app overview page.

<img width="649" alt="Screen Shot 2021-12-18 at 2 49 27 PM" src="https://user-images.githubusercontent.com/59630489/146657548-a5c6dce7-ae1a-479b-b5c6-0eeae92696c2.png">

STEP 5: We need to provide a ‘redirect link’ that we’ll use to collect the user’s permission. From your app’s panel in the developer dashboard, click on ‘Edit Settings’ and add a link under Redirect URIs. This doesn’t have to be a real link: if you don’t have a website, you can simply use

http://localhost:7777/callback

Take note of your client ID and client secret. You’ll find them in the app panel under your app’s name.

If you are still finding it hard to get the access, please refer to this for more information. 
More information : https://developer.spotify.com/documentation/general/guides/authorization/app-settings/

# DATA STRUCTURE AND PROCESSING 

SPOTIFY DATA: 
I created a spotifyAPI class to retrieve the data using the API. I also used the spotipy library to retrieve more specific information. This class contained methods to retrieve albums, artists, specific artist albums, audio features and a general search method as well. The level of challenge was relatively hard because I had to parse through different types of data and levels to get the relevant specific information. I converted the data to a json object. This is a snapshot of the data once retrieved via the API. 

<img width="1341" alt="Screen Shot 2021-12-18 at 12 51 20 PM" src="https://user-images.githubusercontent.com/59630489/146658569-8ee67e15-b327-4726-8969-1aaf84c4c968.png">

I created an empty song list and then sorted through this data to append to the song list. I also extracted audio features from the API and appended the information into the list. I filtered for the top 10 tracks and then this list was then converted into a dataframe. Here is a sample of the dataframe.

<img width="1360" alt="Screen Shot 2021-12-18 at 12 53 43 PM" src="https://user-images.githubusercontent.com/59630489/146658616-11bea3a0-27db-4da9-9b80-b7e100f30bd6.png">

This is the description of the audio features.

danceability — Danceability describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. A value of 0.0 is least danceable and 1.0 is most danceable.

energy — Energy is a measure from 0.0 to 1.0 and represents a perceptual measure of intensity and activity. Typically, energetic tracks feel fast, loud, and noisy.

instrumentalness  — Predicts whether a track contains no vocals. “Ooh” and “aah” sounds are treated as instrumental in this context. The closer the instrumentalness value is to 1.0, the greater likelihood the track contains no vocal content.

liveness — Detects the presence of an audience in the recording.

I analyzed the data to understand the users' musical inclinations. My analysis shows the users' top 10 tracks along with the album covers. I created a radar chart to see which features are the tracks more inclined to and a correlation graph to see the correlations between each of the audio features. I also created a scatterpolt to see the relationship between artists, popularity, energy, and instrumentalness. Here are some of the visualizations. 

<img width="771" alt="Screen Shot 2021-12-18 at 4 01 06 PM" src="https://user-images.githubusercontent.com/59630489/146658803-bb6b4207-4585-4161-bab4-15df51b01fd8.png">


<img width="695" alt="Screen Shot 2021-12-18 at 4 00 46 PM" src="https://user-images.githubusercontent.com/59630489/146658809-56f37d05-faae-4c3e-ad7b-5e62f55cc1a4.png">


<img width="697" alt="Screen Shot 2021-12-18 at 4 00 53 PM" src="https://user-images.githubusercontent.com/59630489/146658811-6275747c-769b-41bb-8123-6f128b86353a.png">


# HOW TO INTERACT WITH THE PROGRAM

In terms of interaction, it is relatively very easy for the user. The user can choose between 'yes', 'no', or 'exit'. 
The user will first be asked if they have a spotify account yet or not. If yes, then the user will be promted to input the CLIENT ID and SECRET CLIENT. If no, then the user will be directed to use the iTunes API. 
For the Spotify API, the user will then be asked if they want to see their top spotify tracks. If 'yes' then their top tracks and album covers will be displayed. Finally, they will be asked if they want to see their musical inclincations or not. If yes, then their respective visualizations and graphs will be displayed. If the user prompts 'no' for any of the interactions(except the first one), the program will thank and end. 


# TAKEAWAYS
