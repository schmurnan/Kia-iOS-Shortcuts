# Kia-iOS-Shortcuts

This project provides a simple API to control your Kia vehicle using the Hyundai Kia Connect API. It includes features such as starting and stopping the climate control, locking and unlocking the car, and listing vehicles.

---
## Intro

This uses the Kia API written in Python. It was developed specifically for iOS shortcuts, though it may also work on Android OS. This allows for shortcuts to:

- Lock Vehicle  
- Unlock Vehicle  
- Start Climate  
- Stop Climate  

This uses the following Python package: [Hyundai Kia Connect API](https://github.com/Hyundai-Kia-Connect/hyundai_kia_connect_api).

---

## Setup

### 1. Create a GitHub repo and Vercel account
- If you don’t have a GitHub or Vercel account, create one.
- Fork this repo or clone it to your own GitHub account.

### 2. Set up Environment Variables
In your project, set up the following environment variables:
- `KIA_USERNAME`: Your Kia username.
- `KIA_PASSWORD`: Your Kia password.
- `KIA_PIN`: Your Kia PIN.
- `SECRET_KEY`: Your Secret Key
- `VEHICLE_ID`: Your Vehicle ID (needed if you have more than one vehicle tied to your account)

### 3. Deploy on Vercel
Once the repo is on GitHub, follow these steps to deploy it on Vercel:
1. Go to [Vercel](https://vercel.com/) and log in with your GitHub account.
2. Click on **New Project** and choose your repository.
3. Set up your environment variables in Vercel’s dashboard:
    - `KIA_USERNAME`: (value)
    - `KIA_PASSWORD`: (value)
    - `KIA_PIN`: (value)
    - `SECRET_KEY`: (value)
    - `VEHICLE_ID`: (value)

### 4. Deploy the project.

### 5. Create IOS Shortcuts
You can create an iOS Shortcut to interact with your Kia Vehicle Control API easily. Follow these steps to set up your Shortcut:

    1. Open the Shortcuts app on your iPhone.
    2. Tap the "+" to create a new shortcut.
    3. Tap "Add Action".
    4. In the search bar, type "Get Contents of URL" and select it.
    5. Set the following options for the "Get Contents of URL" action:
        - URL: Enter the URL of your deployed API endpoint (e.g., https://your-api-url.com/start_climate).
        - Method: Choose POST (or GET if the endpoint requires GET).
        - Headers: Tap "Add New Field" and enter:
            - Key: Authorization
            - Value: YourCustomSecretKeyHere (replace this with your actual secret key).
    6. Tap Next, and then give your shortcut a name, such as "Start Climate" or "Unlock Car."
    7. Tap Done to save the shortcut.
    8. Run the Shortcut: When you run the shortcut, it will send a request to your API, performing the action you configured (e.g., starting the climate control or unlocking the car).

## Notes

The API requires your **region**. By default, it is set to the USA. If you are outside the US, update it using the following region codes:

REGIONS = {
    1: REGION_EUROPE,
    2: REGION_CANADA,
    3: REGION_USA,
    4: REGION_CHINA,
    5: REGION_AUSTRALIA }


The climate command requires a Climate Request Option. By default, it is set to 72°F for 10 minutes, but you can modify this based on your preferences.

---

## Running the Application

Once the environment variables are set, you can run the application in Replit:

bash
Copy code
python app.py

## API Endpoints

GET /: Returns a welcome message.
GET /list_vehicles: Lists all vehicles in your account.
POST /start_climate: Starts the climate control of your vehicle.
POST /stop_climate: Stops the climate control of your vehicle.
POST /unlock_car: Unlocks your vehicle.
POST /lock_car: Locks your vehicle.

## Authorization

For security, each API request must include an Authorization header with the correct SECRET_KEY. Example:

bash
Copy code
Authorization: YourCustomSecretKeyHere

## Notes for Developers

The SECRET_KEY and VEHICLE_ID values are loaded from environment variables to keep sensitive information secure.
If you need to deploy this project on another platform (e.g., Vercel or Heroku), make sure to set up the environment variables there as well.
The app uses Flask for handling requests. You can modify or extend it as needed for additional vehicle control features.

## License

This project is licensed under the MIT License – see the LICENSE file for details.

