# Access Mobile From Desktop

Have you ever wanted to access your Android phone from your desktop PC, or create a mobile mining farm like I do? Then let’s get started. 

# Download
    1. Download the ZIP file from my GitHub repository, the link is in the description below: https://github.com/tarantula3/Access-Mobile-From-Desktop/
    2. Unzip the folder to a location of your choice on your PC.
    3. Open PowerShell "as Administrator" and run the onscreen/following command to enable all PowerShell scripts to run on your PC:
    Set-ExecutionPolicy Unrestricted

# Enable Developer Mode on Your Phone
    1. Go to Settings
    2. About
    3. Software Information
    4. Tap "Build Number" 7 times. (If Developer Mode is already enabled, the system will notify you)
    5. Enter your PIN when prompted, this will enable the "Developer Mode"
    6. Next, turn off the "Auto Blocker"

# Enable debugging
    1. Go back to Settings
    2. Navigate to Developer Options:
        Samsung: Tap the back button
        Motorola: Search for "debugging"
    3. Scroll down until you see "Debugging"
    4. Under Debugging, enable:
        a. USB Debugging &
        b. Wireless Debugging

# Get the IP of your Mobile
    1. Go to Settings
    2. Select Connections > Wi-Fi
    3. Tap the gear/cog icon next to your connected network
    4. Scroll down to view your IP address

# Get Your Phone Ready
    1. Plug your phone into the PC with a USB cable and approve USB access when prompted. Then unplug it.
    2. Make sure your PC and phone are connected to the same Wi-Fi network.
    3. Open PowerShell in the same directory and run the following commands:
        a. .\adb.exe connect $IP
        b. .\scrcpy.exe $IP
        To control multiple phones at once manually, repeat the below command with different IPs:
        c. .\scrcpy.exe -s 192.168.0.xxx
        d. .\scrcpy.exe -s 192.168.0.yyy
    4. Easier way: Just right-click on "EnterIP.PS1" and select "Run With PowerShell"
    5. A window will pop up asking you for your phone's IP - type the IP of your phone in and click OK.

To avoid constantly changing IP addresses when controlling your phones on a regular basis, simply log into your router and set up IP reservation for each device.



# Errors
    1. unable to connect to <ip addr>:5555: cannot connect to <ip addr>:5555: No connection could be made because the target machine actively refused it. (10061)
       Reference: https://stackoverflow.com/questions/37267335/android-studio-wireless-adb-error-10061
        a. stay connect via USB
        b. connect to your WIFI network (computer and mobile device both)
        c. ping DeviceIP (must be have ping to your device)
        d. .\adb kill-server
        e. .\adb usb
        f. .\adb tcpip 5555
        g. unplug usb cable 
        h. .\adb connect yourDeviceIP
        i. adb devices (must be see two device names , one of them is by deviceIP) 
    
    2. Device not reachable 
        a. Ping the IP
        b. Do a MAC to IP mapping on the router
    
    3. To get updated packages manually download them from developers website:
        1. SCRCPY (Windows version) : https://github.com/genymobile/scrcpy > Unzip
        2. SDK Platform-Tools for Windows : https://developer.android.com/tools/releases/platform-tools > Unzip
        3. Copy SCRCPY into SDK folder 
        4. Run Powershell from the same folder 
