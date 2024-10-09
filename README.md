# Language Flashcards

## Overview

The Language Flashcards app is an interactive tool designed to help users learn languages through customizable flashcards. This app connects to a Google Sheets document, allowing users to quiz themselves on a selected list of words in their target language. 

## Features

- Customizable flashcard sets based on user-selected languages.
- Integration with Google Sheets to manage and track vocabulary.
- Text-to-speech functionality for pronunciation practice.
- Progress tracking and scoring system.

## Prerequisites

Before you can publish the app and enable interaction with Google Sheets, you need to set up accounts with RShiny and Google.

### Create an RShiny Account

1. Go to the [RStudio Connect](https://rstudio.com/products/shiny/shiny-server/) page and sign up for an account.
2. Once signed in, navigate to the **Account Settings** section to create a new API token.
3. Save the `.dcf` file that is generated, as it will be necessary for publishing your app.

### Obtain a Google Service Account Token

1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project or select an existing one.
3. Navigate to the **APIs & Services** > **Library** section and enable the **Google Sheets API** and **Google Drive API** for your project.
4. In the **APIs & Services** > **Credentials** section, click **Create Credentials** and choose **Service Account**.
5. Fill out the required fields and click **Create**. 
6. Once the service account is created, click on it to go to the **Details** page.
7. Under the **Keys** tab, click **Add Key** > **JSON**. This will download a JSON file containing your service account credentials.
8. Share your Google Sheet with the service account email (found in the JSON file) to grant access.

## Setup Instructions

1. **Install Required Packages**

   Ensure you have the following R packages installed:

   ```r
   install.packages(c("plyr", "dplyr", "stringr", "janitor", "googledrive", "googlesheets4", "rmarkdown"))
   ```

2. **Modify the Code**

   In your R script, update the following line with your Google service account JSON file path:

   ```
   googlesheets4::gs4_auth(path = 'path/to/your/test-XXXX.json')
   ```

   Also, replace `link` variable with the actual link to your Google Sheet:

   ```
   link <- paste0("https://docs.google.com/spreadsheets/d/YOUR_SHEET_ID")
   ```

3. **Run the App**

   Once you have completed the above steps, you can run the app using:

   ```
   shiny::runApp("path/to/your/app")
   ```

## Usage

1. Launch the app.
2. Select the desired language from the dropdown menu.
3. Choose the number of words you want to test.
4. Click "Start" to begin the flashcard quiz.
5. Use the "Correct" and "Incorrect" buttons to track your progress.
