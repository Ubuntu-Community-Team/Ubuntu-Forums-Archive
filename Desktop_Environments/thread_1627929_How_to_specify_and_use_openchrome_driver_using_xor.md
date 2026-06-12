---
title: "How to specify and use openchrome driver using xorg.xonf"
date: 2010-11-22
forum: Desktop Environments
---

### Post by satyanash on 2010-11-22
Hi,
My computer is an old one, 512MB RAM, 1.3 gHz processor and 64MB of video memory on an on board VIA graphic card. 

Since i could not get the latest Ubuntu 10.04/10 to run on it, i installed Ubuntu 10.04 Server and then did a sudo apt-get install lxde and installed the base LXDE desktop environment on it. Everything runs fine and i have got the sound to work to. 

The problem is that the only resolution i like it in, is 1280x960. The desktop on this resolution is a bit laggy and when i move the windows i get a "Wobbly Windows" effect. (without compiz.. :p) 

Also when i am scrolling down on long webpages or pages with a lot of text it again has those cutty and laggy effect. I thought this might be a problem of incorrect drivers and decided to get the Openchrome drivers(which were not included by default since this is a server installation). 

After apt-getting them, i wanted to change the driver specified in the /etc/X11/xorg.conf file from vesa to openchrome. When i searched for the xorg.conf file it was not there i tried locating it using locate -i xorg.conf, and have found only one result that seemed to make sense /etc/X11/xorg.conf.failsafe. 

I opened it up and found out that it had a section called driver in it and it was specified as vesa. 

After some googling i found out that i could boot into a live CD and copy the xorg.conf from there and edit it, and put it here and X would use it the next time the computer starts.

When i booted the live CD, there too was no xorg.conf file. Then just to try it out, i took the /etc/X11/xorg.conf.failsafe file copied it and named the copy xorg.xonf. And changed the driver in it to openchrome from vesa and rebooted. 

After rebooting the computer did not encounter any errors related to a faulty xorg.conf file nor did it have any problems in booting. But it still has all that laggy windows and everything. So i cant figure out whether it actually is using the openchrome driver or has it automatically detected everything, just like it did earlier.

Please reply..
Thanks in advance.

---

### Post by satyanash on 2010-11-22
Just to see what it was and how it was i tried this script out: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

And when i ran it, it said 

"At least one check had to be skipped:
 Error: openchrome driver in use "

So by this i can at least be sure that openchrome driver is being used and that it has accepted my xorg.conf file.

But i still haven't stopped getting the laggy effect.

Please help me..

---

### Post by SteveDee on 2010-11-22
On Ubuntu 10.xx you only add a xorg.conf file for your own settings. So I guess in your case this file should only contain something like this:- ```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
	option		"DRI"	"off"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection


```
...but with "Intel" replaced by your driver name, and driver options to suit whatever settings you need. By experimenting with these settings you should be able to tell if the system is using this file.

---

### Post by satyanash on 2010-11-22
i have been able to figure out that whether my system is using the driver or not.. but it still get that laggy effect.

and the effect is the highest at the highest resolution(1280x960)..and the none at the lowest resolution(640x480). i prefer the 1280x 960 than 1024x768, 800x600, 480x680. the last to are not good fr everyday use and 1024x768 is still too big..

but thanks for the reply.

---

### Post by SteveDee on 2010-11-22
> **sattu94@gmail.com said:**
> .. but it still get that laggy effect....


I think its probably due to the limitations of your hardware. My laptop is a similar spec; 1.4GHz, 750MB RAM, but 1024 x 768

If I run System Monitor, select the Resources tab, and then drag a window around the screen for a few seconds, the cpu usage sits at 100%...see what happens on your system.

---

### Post by satyanash on 2010-11-22
on my system, as you said the same thing happens, but only when on linux, when i am on windows i never encounter such laggy effects..that is what makes me think that it might not be a hardware limitation..

---

