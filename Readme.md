# Pressure Sensor's Interface Set-Up

For its setting up a Raspberry Pi is needed, together with a SD card. In our case, the interface has been developed using a Raspberry Pi 4 Model B and a SD card of 32 GB.

**1º - OS Installation:** Install in your SD Card the Operating System for your Raspberry Pi 4 Model B. You will need a SD card, and its corresponding lector, where the OS will be installed. Then, the raspberry pi imager software must be installed in a PC, from which the corresponding OS will be written into the SD card. 
We recommend you to follow the instruction in the official documentation web of raspberry image OS installation.

**2º - Interface dependencies:** Once Debian 10 is installed in the raspberry, connect it to the internet and download this repository. Then, in the corresponding path, download the following dependencies:
*	Ensure that everything is **up to date**
		
		$ sudo apt update
		$ sudo apt-get dist-update
*	Install **NodeJs** and its package manager (**npm**):
		
		$ sudo apt install nodejs npm
* Install **Server**:
		
		$ sudo apt install mariadb-server

**3º - Interface documentation**:  Once everything is up to date and installed, download all interface files from this GitHub link. We recommend you to clone the repository via “git clone”. Then, go to the main folder (../your_path/pressure-sensor), and introduce the following instructions.
* Install **Bluetooth** dependencies:

		$ sudo apt-get install build-essential libbluetooth-dev  
* Install the dependencies to the local **node_modules** folder and **rebuild** project:

		$ npm install
		$ npm rebuild
		
**4º - Interface automatic launch**: Configure the interface to be launched automatically at RPi boot. Thus, the interface will be accessible as long as the Raspberry is connected. In case of an interface error occurs, plug-off and plug-in again the RPi should solve it.
* **Open** /etc/rc.local:

		$ sudo nano /etc/rc.local
		
* At the end of the file **add** the following:

		sudo node /your_path/pressure-interface/index.js &

**5º - Wireless Access Point**: Configure the raspberry pi as WiFi access point to access the interface from other device’s browsers. We recommend you to follow the raspberry pi official documentation [Setting up a Raspberry Pi as a routed wireless access point](https://www.raspberrypi.com/documentation/computers/configuration.html) in case you are using a Raspberry Pi 4, or [this link](https://pimylifeup.com/raspberry-pi-wireless-access-point/comment-page-1/), in case of Raspberry Pi 3 model.  

**6º - Pair Bluetooth sensors**: As last step, you must pair, with the RPi, the Bluetooth devices that you will use with the interface. For this purpose, please, open a terminal and follow the following instructions:

		I.	$ sudo bluetoothctl
		II.	[Bluetooth]# default-agent
		III.	[Bluetooth]# scan on   (Here you must see the sensor name and MAC)
		IV.	[Bluetooth]# pair 99:99:99:99:99:99   (Sensor´s MAC address)
		V.	[Bluetooth]# trust 99:99:99:99:99:99  (Sensor’s MAC address)
		Steps IV and V must be introduced while scan is on. Please, repeat this two steps for each sensor you will use.

