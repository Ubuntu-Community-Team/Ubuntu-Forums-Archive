---
title: "Latitude 2100 TouchScreen driver bug."
date: 2009-07-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by minilatitude on 2009-07-31
Latitude 2100 TouchScreen fail,  for instance, it often fail with drag operation over scrollbars or touching and draging the "standar resise window icon". 
When fails, the system hung up, and the only way to recover is pressing 5 secons the power-off button.

I upgrade my system to ubuntu 9.04 and reinstall the driver (downloaded from dell: Ideacom uts6680 IC- touchScreen utility) and the problem remains.

I think there are a bug into the touchscreen-driver.

---

### Post by caprilo on 2009-12-29
I also have this problem. The touchscreen works fine when only pushing buttons, but when you drag, the whole system freezes, and not even the SysReq key combination works. It's a simple feature as to collapse the whole system; the worse is that it came "configured" with my machine.

---

### Post by ksa618 on 2010-01-22
I've got this problem too. When the system freezes I'm still able to access it from another computer using ssh. However I can't seem to find any relevant information as to why it froze in any log files.

---

### Post by gdoutch on 2010-01-24
I get the same too.

Has anyone here seen this?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/412704](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/412704)

---

### Post by fauzii on 2010-02-04
I did this:  

Step 1) Get the drivers: Go to Welcome to Dell Support, go to driver downloads, select your mode(Latitude 2100), select Ubuntu Desktop Edition 9.04 as the OS, and download the ideacom touchscreen drivers. In my case, the file was called welch_touchscreen_ubunt9.04.tgz. Extract them to whatever folder you like. I chose ~\Downloads, and will use this folder throughout.   

Step 2) Stop GDM and X, get an Xorg.conf. Press CTRL+ALT+F1 to change to TTY1 (Virtual Terminal). Log in using your normal username and password. Stop gdm with the following command: &quot;sudo service gdm stop&quot; You will be asked for your password.  Next, type &quot;sudo Xorg -configure&quot; to create an Xorg.conf. It will be generated in your home directory (~), and it will be called xorg.conf.new. Type &quot;sudo mv ~/xorg.conf.new /etc/X11/xorg.conf&quot; to move it to the correct folder in etc for the driver. Press CTRL+ALT+F2 to get to TTY2. Log in there, and type &quot;sudo Xorg&quot; to start X for setting up the touchscreen. You will need to enter your password. Press CTRL+ALT+F1 to change to TTY1 again.   

Step 3) Install the drivers: find where you put the files (again, in my case ~/Downloads/), and do &quot;cd debs/main/&quot;. Run &quot;sudo -s&quot; and enter your password again (if needed). YOU ARE NOW ROOT. BE VERY CAREFUL. As root, run &quot;DISPLAY=:0 dpkg -i idc-touch*.deb&quot; to install the driver. The DISPLAY=:0 bit is to tell the driver where your X session from before is running. Hit CTRL+ALT+F1 to get to TTY1. Make sure dpkg finished succesfully and with no errors. Hit CTRL+ALT+F2 to get back to TTY2. Press CTRL+C to kill the Xorg server. Type &quot;sudo service gdm start&quot; to restart GDM. Log in. Run the calibration utlitiy now found under Applications->Accessories->Touch Screen (Likely near the bottom.) You will need to type in your password.   

Step 4) Reboot: Reboot (sudo reboot) to make sure the touchscreen maps correctly in udev. Log in to your Gnome Desktop. Test your touchscreen. Recalibrate if needed. RECALIBRATION DOES NOT REQUIRE A LOG OUT WITH THIS DRIVER! It takes effect immediately, unlike the previous evtouch driver.   

That fixed it in 9.10 UNR.  I found that info in this post: 
[http://www.mydellmini.com/forum/dell-latitude-2100/9414-latitude-2100-ubuntu-linux-2.html](http://www.mydellmini.com/forum/dell-latitude-2100/9414-latitude-2100-ubuntu-linux-2.html)

---

### Post by deadhp1 on 2010-02-26
I can also confirm that the bug exists still on both 9.04 and 9.10.
If you only use the touchscreen and not the mouse or touchpad then you will run into it sooner or later. 
I also have a Clarion Mind which uses the same touchscreen driver, but on psaux.  It also has the same bug.

---

