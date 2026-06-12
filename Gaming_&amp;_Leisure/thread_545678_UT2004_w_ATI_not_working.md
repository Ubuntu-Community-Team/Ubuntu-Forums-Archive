---
title: "UT2004 w/ ATI not working"
date: 2007-09-07
forum: Gaming &amp; Leisure
---

### Post by Blaaguuu on 2007-09-07
I am trying to get UT2004 working with my ATI 9700 Pro card, and having a hard time... I should start by saying that I am a complete beginner with Linux.

The other day I installed UT2004 off my DVD and it worked, but with the default drivers that Ubuntu used i was getting terrible FPS. So i decided i would try using the ATI proprietary drivers, and see how those worked. I actually totaly reinstalled Ubuntu 7.04 for other reasons, before using the Envy GPU driver tool to get the latest ATI drivers, then installed UT2004 again... But now when i run the game, the splash screen comes up for a bit, then disapears, btu the game never starts.

Anyone have any idea what is going on, or how i can fix it, and get UT2004 running with halfways decent FPS?

Thanks! I am lookign forward to using Ubuntu a lot in the future if I can figure some stuff out ;)

---

### Post by Gillen on 2007-09-08
I have been playing UT2k4 on Ubuntu since 6.04 with no real problems using at first an X600 and now a X1650 Pro on 7.04. I have always setup the ATI drivers as follows.

To install ATI Radeon Drivers

sudo gedit /etc/X11/xorg.conf

Copy the following to the xorg.conf and save

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

Save the file,  then the following.

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

then REBOOT

Installing UT2k4 and being from Windows I have installed the game by dragging the linux-installer.sh from the DVD to my desktop opening Properties and clicking "Allow executing file as program" under Permissions Tab, close then double click and Run. The installer launches and I change the destination install path to my home folder /home/name/games/ut2004 I don't install links or menu shortcuts.
When it finishes I patch to our server version and launch the game from the folder by double clicking the ut2004 file after first changing the file Properties and clicking "Allow executing file as program" under Permissions Tab.
After reading a ton of posts I have always done it this way I know its not the Linux way but it works.
The X600 gave reasonable frame rates average 50 to 60 depending on the map. If I remember correctly the X600 is not that much different from the 9700 Pro so you should get good playable frame rates depending on how you tweak the game settings.
The last time I used Envy to install the August 07 (8.40) drivers I was not impressed 3D was OK but DVD playback was a flip chart and the screen resolution choices were wrong so I reverted back to the Ubuntu supported drivers as above.
The truth is ATI drivers for Linux are not as good as the windows versions but that I think is changing with 8.42. I am sticking with ATI as I have always had problems with Nvidia the last an 8400 was a piece of rubbish and I had to jump through too many hoops just to get it working and the 3D performance under linux was utter rubbish.
By the way to get the game to play anywhere near as smooth as windows and using a hi res laser mouse I had to mess with the mouse polling as follows.

gksudo gedit /etc/modules

Add these two lines onto the end of the file.

-r usbhid
usbhid mousepoll=1

Well I hope this helps.

Regards. Steven.

---

### Post by Cappy on 2007-09-08
> **Gillen said:**
> 
-r usbhid
usbhid mousepoll=1


Only use 1 if you have a:
Microsoft Habu
Razer Copperhead
Razer Krait
Razer Viper
Razer DiamondBack


Otherwise use a 2.

Using a polling number that is too low can cause unstable polling times which isn't good for input accuracy and can possibly damage the mouse.

More about mouse polling can be found here:
[http://ubuntuforums.org/showthread.php?t=392494&highlight=polling](http://ubuntuforums.org/showthread.php?t=392494&highlight=polling)

---

### Post by Blaaguuu on 2007-09-08
Thanks for the replies.

But I uninstalled the ATI drivers, and followed your instructions, but UT2004 still doesn't get past showing the splash screen...

---

### Post by Cappy on 2007-09-08
Open a terminal at Applications-->Accessories-->Terminal
and type
```
ut2004
```
and paste the error message back just in case it is something else.

---

### Post by Blaaguuu on 2007-09-08
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual

History: 

Exiting due to error

---

### Post by Gillen on 2007-09-08
Hi Blaaguu,

Sorry it did not work for you but not being long in this game I have told you all I know. Silly question but if you are using Fiesty did the Restricted Drive Manager pop up and ask you to enable the driver with a check box. I am sure someone will come up with an answer for you, they are a friendly lot here in Ubuntu land.

Regards. Gillen.

---

### Post by Gillen on 2007-09-08
Cappy,

Thanks for the information on mouse polling I have a generic laser mouse with a 1600 dpi res. I was looking for a way to make the game run smooth and I cam accross your previous posts and tried the suggestions, 2 gave poor results so I changed it to 1 and it smoothed things out a lot though still not up to win2k standards if the truth be told.  Our server runs the game at 135% speed so response time needs to be good, the mouse I have though it was not expensive works excellent under win2k. The whole input routine in Ubuntu Feisty does not seem lend itself to smooth game play in UT2k4, beside mouse polling I think keyboard responce is not correct though I have not seen any post about that. One thing I would ask, before I used your suggestions the mouse was not very smooth and tended to jump about now it is rock solid and is quite smooth however when a new player joins the server I can suddenly find myself looking at the floor or ceiling any suggestions about that?

Regards. Gillen.

---

### Post by Blaaguuu on 2007-09-08
First, thanks for the help, guys... I did a little additional searching, and fooled around with a few things, then went through the above driver installation again, and everything seems to be working great!

One additional question, relating to the mouse movement, though... is there any way to get "Mouse Smoothing" to work within UT2004? i have it checked in the options, but it doesnt appear to do anything. I am used to using it on my windows rig, so im havign a hard time aiming without it.

Thanks again!

---

### Post by Cresho on 2007-09-08
you should tell us what mouse you are using!

i am using a logitech mx518 with these settings in xorg.conf

in terminal do this

sudo gedit /etc/X11/xorg.conf

and input this under Section "inputDevice" or replace.

this gets all my buttons working.

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Resolution" "800" #optional
Option "Buttons" "10"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
EndSection

---

### Post by Blaaguuu on 2007-09-09
I have an MX510, and here is my xorg.conf mouse setup:

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Resolution" "800" #optional
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
	Option "Buttons" "7"
	Option "ButtonMapping" "1 2 3 6 7"
EndSection

I still dont notice any difference with Mouse Smoothing checked/unchecked, though. Is it maybe a feature that just wont work in the linux environment? perhaps something related to DirectX?

---

