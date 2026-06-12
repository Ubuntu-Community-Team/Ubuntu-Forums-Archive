---
title: "PC shutdown when playing WoW"
date: 2009-04-08
forum: General Help
---

### Post by Kildahl on 2009-04-08
Hi

First of all, I am very very new to all this ubuntu 8.10, but I sincerely hope some of you can help me out!

Everything have been working so far, Ubuntu is running, its looking gr8, installed WoW (took some time because I'm new to this - also because of the editing in config.wtf and regedit...), and the FPS is much better than on Vista. Vista 3 - 18 fps. Ubuntu 30 - 50.
(regarding the FPS, it starts of quite well. Some 60-72 or so. Then it starts to drop to the 30-50.)

However. When I'm playing, the PC just simply shutdown randomly. Sometimes it just restarts.
It can happen after 5 min. of gameplay or after an hour.

This is EXTREMELY frustrating!

I was afraid that it could be the graphics driver as my card is the ATI Radeon Mobility X1600 and it is on proprietary driver. But with the gr8 FPS (compared to in Vista) I can't understand if that's the case.
 - But then again, It have now also happened while I was watching a vid on the net.

Can anyone help a desperate person out? 
 - And what info do you need to have to help me out?

---

### Post by 3rag0n on 2009-04-08
> **Kildahl said:**
> Hi

First of all, I am very very new to all this ubuntu 8.10, but I sincerely hope some of you can help me out!

Everything have been working so far, Ubuntu is running, its looking gr8, installed WoW (took some time because I'm new to this - also because of the editing in config.wtf and regedit...), and the FPS is much better than on Vista. Vista 3 - 18 fps. Ubuntu 30 - 50.
(regarding the FPS, it starts of quite well. Some 60-72 or so. Then it starts to drop to the 30-50.)

However. When I'm playing, the PC just simply shutdown randomly. Sometimes it just restarts.
It can happen after 5 min. of gameplay or after an hour.

This is EXTREMELY frustrating!

I was afraid that it could be the graphics driver as my card is the ATI Radeon Mobility X1600 and it is on proprietary driver. But with the gr8 FPS (compared to in Vista) I can't understand if that's the case.
 - But then again, It have now also happened while I was watching a vid on the net.

Can anyone help a desperate person out? 
 - And what info do you need to have to help me out?



Does ur comp shutdown in an instant,... or does it look as if it were shutting down normally (i.e., like when you tell the system to actually shutdown) ?...

In a normal shutdown, opened windows will close and then the shutdown splash will appear...

in an abnormal death the screen might get corrupted and it might shutdown in an instant...

So just explain the "symptoms" when the anomaly occurs.

---

### Post by 3Miro on 2009-04-08
Is there any specific ATI tool for monitoring temperature. NVIDIA has the NVIDIA control panel, I don't know about ATI. It is possible that the video is overheating and the system just shuts down to prevent damage.

---

### Post by Kildahl on 2009-04-08
It shutdown in an instance. No warning given, no nothing.

That also happens when it restarts. *Edit - If it restarts instead.*

The screen goes black, and if it shutdown i have to start again (obviously). 
If it restarts, it goes immediately, after the "shutdown", into starting up again. - again, its instant and doesn't care about logging out, shutting down windows, etc.

It's basicly like if I plug the power supply on a "normal" computer. (I'm on a laptop though).

---

### Post by Kildahl on 2009-04-08
Hi 3Miro

That's actually an interesting point of view. I have been DL the Driver from LG and I have something called ATI Catalyst Control Center. If I remember correct that's just for setting up different graphical performances.

I don't have any program installed for checking the heat. Do you know where I can DL something to check that?

Btw. You guys are fast in here :-P thx.

*Edit: The ATI Catalyst Control Center, I can't get into that, so I can't really see what it does anymore. Had it installed while I was on Vista, but it's been a while since I've been in there.*

---

### Post by 3Miro on 2009-04-08
[http://www.overclock.net/faqs/108855-how-enable-temperature-monitoring-ati-tool.html](http://www.overclock.net/faqs/108855-how-enable-temperature-monitoring-ati-tool.html)

[http://www.phoronix.com/scan.php?page=article&item=286&num=1](http://www.phoronix.com/scan.php?page=article&item=286&num=1)

Those are old links. Look for something like that in the repositories (i.e. search for ATI and/or AMD) or go to the AMD web-page.

Heat on a laptop is generally a problem. Install the tool to check. If this is the case, you can try to buy a cooling pad. (Low FPS under Vista could also be caused by heat problem)

---

### Post by Kildahl on 2009-04-08
Thank you 3Miro! Downloading now :P

I remember when I got the computer, there was nothing really, and could play at almost best graphics with almost no lag.

Now, even after I had my com run a format and reinstalled Vista it would lag severely. Then I installed Ubuntu last week, and the lag is almost gone. However this restart/shutdown is soooo frustrating!

---

### Post by anlag on 2009-04-08
Really sounds like an overheating problem. You could also try to physically clean your computer a bit, ie getting dust out of the fans and the like. That kind of thing would get worse over time and could explain your decreasing performance.

---

### Post by Yashiro on 2009-04-08
Linux doesn't usually crash in this way. This suggests you have a hardware problem.
Most likely your video card or cpu is overheating.

If you're using ati catalyst drivers, try running this in a terminal before starting your game.
> aticonfig --pplib-cmd "set fanspeed 0 75"

---

### Post by Kildahl on 2009-04-08
I have DL ATItool 0.26 but I can't run it. It gives me an information window where it says:

The Kernel Mode Driver does not seem to be running.

A device is required for cuminication with your video hardware.

If you just upgraded from an older version it may help to uninstall ATITool, reboot, then install the new version.
---------------
However, when I click 'OK' it does give the ATITool window. 
I can make a new profile.
The Core and Memory shows 0 though. and press much except for Scan for Artifacts and Show 3D View, Settings, and the load, save, new, delete, properties. The last 5 is for the profile.
----------------

SO. I have checked around the internet, and DL KSensors and LM-Sensors. 
Ksensors I can't figure out what says, or more correctly can't understand what is what :D

Here it is though:

CPU STATE:
Idle 75.0 - 84.9
Sys 5.0 - 21.5
Nice 0.0
User 7.5 - 10.9

-----------------
I have also used the command acpi -t in the terminal and it says:
   
     Battery 0: Discharging, 99%, discharging at zero rate - will never fully discharge.
     Thermal 0: ok, 40.0 degrees C
     Thermal 1: ok, 68.0 degrees C
     Thermal 2: ok, 73.0 degrees C
-----------------

If i write 

aticonfig --pplib-cmd "set fanspeed 0 75"  

the Terminal says the following:

Parse error on line 34 of section Module in file /etc/X11/xorg.conf
	"Disable" is not a valid keyword in this section.

------------------
LM-Sensors, I just don't know what that really does or how to use it. can't even find it after it's installed :S
------------------

Also have I installed something called Computertemp or cputemp. But I can't figure out how this works either :S


As I said, Linux is very new to me ...

---

