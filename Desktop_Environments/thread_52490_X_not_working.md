---
title: "X not working"
date: 2005-07-27
forum: Desktop Environments
---

### Post by arcanistherogue on 2005-07-27
I edited the /etc/X11/xorg.conf file using a guide i found here, in order to configure the buttons on my MX510.  the exact link is: [http://www.ubuntuforums.org/showthread.php?t=28374&highlight=mx+510](http://www.ubuntuforums.org/showthread.php?t=28374&highlight=mx+510)

I edited the data just as the guide said, but when i boot up it goes into a command line login.  i typed in  "startx" and it said there was an error in the xorg.conf file. something to do with the mouse, that the data was incomplete or something.  I reset it to the original stats said in the guide, but it still said it was messed up.  

Is it because i have a USB to PS/2 converter on my mouse?  it says in the conf file mouse.usb, and i remember it being something before that before i switched....

---

### Post by heimo on 2005-07-27
My PS/2 mouse section of xorg.conf:

```
Section "InputDevice"
		Identifier	  "Configured Mouse"
		Driver		  "mouse"
		Option		  "CorePointer"
	    Option		  "Device"			    "/dev/input/mice"
	    Option		  "Protocol"			  "ImPS/2"
	    Option		  "ZAxisMapping"		  "4 5"
EndSection

``` 

Search /var/log/Xorg.0.log for errors and warnings. You can also always reconfigure X using
 ```
sudo dpkg-reconfigure xserver-xorg

``` 
I suggest making backup of the configuration file before any changes.

---

