# Pi3OneDrivePowerBI
Storing data for a Raspberry Pi3 on OneDrive and Visualising that data in PowerBI

Most applications that visualise their data in PowerBI do this through Azure Stream Analytics Jobs or Web Apps.  Whilst this is a perfectly suitable solution, it can also be quite expensive.  By way of example, a recent project that I completed measured the temperature and humidity of a laboratory, sent that data via a JSON string to an IoTHub, created a Stream Analytics job and finally visualised that data in PowerBI.  This cost around A$60 per month...quite expensive for a single, simple app.

PowerBI is able to read data from a variety of sources, local files and OneDrive included.  You can use PowerBI to visualise the local data but it does not auto (or manual) refresh.  Pulling the data from OneDrive or OneDrive for Business does allow for auto refresh, albeit once an hour, but does allow for manual refresh whenever you want.

Achieving this is quite simple and involves the following steps;
  1. Connect Raspbian to your OneDrive account and create a local OneDrive directory.
  2. Write a program to store the measured data into the local OneDrive folder and allow it to sync to the cloud.
  3. Use PowerBI to get the datastream from your OneDrive account and create the reports and dashboards.
  
I'm going to assume that you have the following;

  1. A functioning Raspberry Pi 3 with Raspbian installed.  
  2. You are able to connect remotely to the Raspberry Pi 3...I installed XRDP on the Raspberry Pi3 which allowed me to use the native Remote Desktop Connection facility in Windows.  
  3. That you have some form of file transfer system installed, I use FileZilla.

So let's get started...

1. Connect Raspbian to your OneDrive account and create a local OneDrive directory.
   
   There is a very good explaination for this step at http://www.avoiderrors.net/how-to-sync-microsoft-onedrive-in-linux so I wont duplicate this step her except to say that in step 2 when it askes if you want to change the default directory, type Y and then accept the default directory location.  If the directory fails to sync the open a terminal window, navigate to the onedrive-d folder and type onedrive-d stop...allow the command to complete then wait a few seconds and then restart by typing onedrive-d start.  The folders should now sync.
