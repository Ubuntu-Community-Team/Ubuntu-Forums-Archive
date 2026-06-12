---
title: "can not get my ZTE MF627 usbmodem working"
date: 2009-03-20
forum: General Help
---

### Post by pc_doc on 2009-03-20
Hi, i'm use ubuntu 8.10 and i have ZTE MF627 mobile broadband usb modem whith i can not get working.
When i plug it in the lights on the modem go red then green but no wizard comes up to configure it. Does anyone know if this modem is working in ubuntu.
I did see a a picture in Linux Format mag showing them using Ubuntu 8.10 with a usbmodem and it said that ubuntu can now configure it using a wizard when you plug it in.

---

### Post by pc_doc on 2009-03-21
can no one help with this ?

---

### Post by GeorgeVita on 2009-03-22
Hi **pc_doc**, your modem ZTE MF627 is not listed into file:
/usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
(MF626, MF628 and MF632 exist)

so you probably have to "trim" some parameters.

At first plug your modem to the USB port, wait 10-15 seconds, open a terminal window and execute the command: **lsusb** 
Copy paste here the line: **Bus 00x Device 00x: ID 19d2:YYYY** to see how the system recognizes the modem.
Also read my post #8 [http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934)

Regards,
George

---

### Post by pc_doc on 2009-03-23
> **GeorgeVita said:**
> Hi **pc_doc**, your modem ZTE MF627 is not listed into file:
/usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
(MF626, MF628 and MF632 exist)

so you probably have to "trim" some parameters.

At first plug your modem to the USB port, wait 10-15 seconds, open a terminal window and execute the command: **lsusb** 
Copy paste here the line: **Bus 00x Device 00x: ID 19d2:YYYY** to see how the system recognizes the modem.
Also read my post #8 [http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934)

Regards,
George

Ok George i will try that when i get in from work later today

---

### Post by pc_doc on 2009-03-23
ok this is what lsusb gives me

Bus 005 Device 005: ID 19d2:0031 
Bus 005 Device 003: ID 10f1:1a08 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 003: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
[alan-deb@alan-deb-laptop ~ 
->

---

### Post by GeorgeVita on 2009-03-23
Looks like in my case with ZTE MF636,

**Bus 005 Device 005: ID 19d2:0031**

so follow instructions from **post#8** of:
[http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934) (steps 3, 4 and 5)

G

---

### Post by pc_doc on 2009-03-23
> **GeorgeVita said:**
> Looks like in my case with ZTE MF636,

**Bus 005 Device 005: ID 19d2:0031**

so follow instructions from **post#8** of:
[http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934) (steps 3, 4 and 5)

G
Ok i will try that now many thanks;)

---

### Post by pc_doc on 2009-03-25
> **GeorgeVita said:**
> Looks like in my case with ZTE MF636,

**Bus 005 Device 005: ID 19d2:0031**

so follow instructions from **post#8** of:
[http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934) (steps 3, 4 and 5)

G
**SOLVED**
I have got this working at last thanks to this link many thanks for your help GeorgeVita

---

### Post by donwinchell on 2009-04-01
I did not get any wizard when I plugged in a bell mobile (Canada) cell wireless card.  but I went to network, edit connections (right click on network icon) then went to the broadband tab. I did don't know if I entered it or if it was defaulted, but #777 showed up in the "number" and under username I put in the cell number assigned to the card by the cell carrier.

worked slicker than ----- through a goose.  worked faster and cleaner than the software that came with the card for windows.

maybe this will help

don

---

### Post by jpsugden on 2009-04-13
Hi, cant gey my zte627 to work on dell mini/ubuntu. Have followed threads elsewhere and dmesg shows
[ 3631.921840] usb 5-8: new high speed USB device using ehci_hcd and address 10
[ 3632.069610] usb 5-8: configuration #1 chosen from 1 choice
[ 3632.074766] scsi9 : SCSI emulation for USB Mass Storage devices
[ 3632.075355] usb-storage: device found at 10
[ 3632.075367] usb-storage: waiting for device to settle before scanning
[ 3635.027517] usb 5-8: USB disconnect, address 10
[ 3639.263514] usb 5-8: new high speed USB device using ehci_hcd and address 11
[ 3639.412143] usb 5-8: configuration #1 chosen from 1 choice
[ 3639.415162] scsi10 : SCSI emulation for USB Mass Storage devices
[ 3639.416601] usb-storage: device found at 11
[ 3639.416620] usb-storage: waiting for device to settle before scanning
[ 3643.263604] usb-storage: device scan complete
[ 3643.265593] scsi 10:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[ 3643.268606] scsi 10:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[ 3643.274368] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[ 3643.274562] sd 10:0:0:0: Attached scsi generic sg1 type 0
[ 3643.322669] sr0: scsi-1 drive
[ 3643.322813] sr 10:0:0:1: Attached scsi CD-ROM sr0
[ 3643.322915] sr 10:0:0:1: Attached scsi generic sg2 type 5
[ 3654.210256] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 3654.214346] ISOFS: changing to secondary root
Help. Im new to this so it needs to be real basic

---

### Post by GeorgeVita on 2009-04-13
Hi **jpsugden**,

we must see how the system sees the modem, so additional info could be found with:

Boot without the modem, wait for the system to stabilize, plug your modem to the USB port, wait 10-15 seconds, open a terminal window and execute the command: **lsusb**

Copy paste here the line: **Bus 00x Device 00x: ID 19d2:YYYY**

Also read my post #8 [http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934)

(above are a copy of post#3 of this thread)

Regards,
George

---

### Post by jpsugden on 2009-04-13
jonathan@jonathan:~$ lsusb
Bus 005 Device 003: ID 19d2:0031  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
jonathan@jonathan:~$ Bus 00x Device 00x: ID 19d2:YYYY
bash: Bus: command not found
jonathan@jonathan:~$

---

### Post by GeorgeVita on 2009-04-13
> **jpsugden said:**
> jonathan@jonathan:~$ lsusb
Bus 005 Device 003: ID 19d2:0031  
...

OK, system seems to identifies your modem as **vendor=19d2** (ZTE) and **product=0031**

Are you using Ubuntu 8.10?
Right Click on the 2 PC screens (up right on the top line "panel") and then click **About**. What is the version of Network Manager?

...and a tip: You can Add some "icons" to the top panel:

1. From Applications, Accessories, right click Terminal and click to Add this launcher to panel.
2. From Applications, Accessories, right click Text Editor and click to Add this launcher to panel.
3. From System, Administration, right click System Monitor and click to Add this launcher to panel.

Now you can just click the terminal icon to open it, or later it will be more convenient to know the 3G data traffic from system monitor.

[B]Can you follow instructions from post#8 of:
[http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934) (steps 3, 4 and 5)?[/B]

G

---

### Post by jpsugden on 2009-04-14
I am using 8.04+ LTS and nm-applet 0.6.6.
I followed #1 of the How to - ubuntuforums.org/showthread.php?t=1017630.
When I plug in the dongle it goes red, then off, then red and then green where it stays

---

### Post by GeorgeVita on 2009-04-15
> **jpsugden said:**
> I am using **8.04**+ LTS and nm-applet **0.6.6**.
I followed #1 of the How to - **ubuntuforums.org/showthread.php?t=1017630**.
When I plug in the dongle it goes red, then off, then red and then green where it stays

As per above, Ubuntu 8.04 which has NM 0.6 and you have the **019d2:0031** (from above post), I propose to use the **wvdial** method for connecting.

You have to set some parameters to the configuration file **wvdial.conf**
First determine the port that uses your modem. From a terminal window type: **ls /dev/ttyUSB*** and press <ENTER>
You must see /dev/ttyUSB0 /dev/ttyUSB1 /dev/ttyUSB2 and possibly /dev/ttyUSB3
The usable port is this with the **higher** number. You may use this below:

Open a terminal window and type: **sudo gedit /etc/wvdial.conf** and press <ENTER>
give your password if asked (not shown while you type it) and press <ENTER> again.

A window will open with the title **wvdial.conf (/etc) - gedit**
There you should delete any existing line (use the mouse to select and DEL to delete).
Copy and paste the following lines (shown in bold) into that window:

[B][Dialer Defaults]
Modem = [COLOR="Red"]/dev/ttyUSB2[/COLOR]
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = [COLOR="Green"]user[/COLOR]
Password = [COLOR="Green"]pass[/COLOR]
Phone = *99#
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 =AT+CGDCONT=1,"IP","[COLOR="Green"]internet[/COLOR]"
[/B]

Change the port number (shown in red) with the higher one, found in the previous command.
Click on SAVE icon and close this (gedit) window.
Another **note**: Above are generic Username, Password and APN (shown in green). Check them with your provider, or gime me more data to search also (country, provider, type of account).

Boot the system without the modem, wait for the system to stabilize (till all panels and icons appear), attach your modem, wait 20 seconds, open a terminal window, type:
**sudo wvdial** and press <ENTER>

If all are OK you will see some text lines including:
**CONNECT xxxxxxx**
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at ...
--> Pid of pppd: ...
...
--> **local IP** address ...
...
--> **primary DNS** address ...
...
**The connection done!** Click on Firefox icon, remove **Work Offline** mode with **ALT+F W** and browse.

To **disconnect** press **CTRL+C** at the window you got connected.

In case of any error copy & post here ALL terminal messages starting from your sudo wvdial command till the final terminal prompt.

Regards,
George

---

### Post by jpsugden on 2009-04-16
George, problem at the start!
jonathan@jonathan:~$ ls /dev/ttyUSB*
ls: cannot access /dev/ttyUSB*: No such file or directory
jonathan@jonathan:~$

Have tried various ie no space but still the same message
Regards JS

---

### Post by GeorgeVita on 2009-04-21
> **jpsugden said:**
> George, problem at the start!
jonathan@jonathan:~$ ls /dev/ttyUSB*
ls: cannot access /dev/ttyUSB*: No such file or directory
jonathan@jonathan:~$

Have tried various ie no space but still the same message
Regards JS

Another try to help!

From terminal: **lsusb**
When you see among respond lines one including: **19d2:0031** try the command:
**sudo modprobe usbserial vendor=0x19d2 product=0x0031**

Remove and attach again the modem. Close any auto-run window. After 15 seconds run: **ls /dev/ttyUSB***

You must see: /dev/ttyUSB0 /dev/ttyUSB1 /dev/ttyUSB2 and possibly /dev/ttyUSB3
If not "I quit!", else follow info about configuring wvdial.

Regards,
George

---

