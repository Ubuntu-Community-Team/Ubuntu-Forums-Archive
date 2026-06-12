---
title: "DVD - no picture +only sound when run with sudo"
date: 2005-04-12
forum: Desktop Environments
---

### Post by department27 on 2005-04-12
Hi I have a strange problem.

I have tried Totem, gxine and kaffeine, and they all give the same results. When I try to play a dvd or wmv, etc I get no sound or picture.

When I run any of the apps as sudo I get sound but no picture.

Have all the latest software, libdvdcss, etc.

What is going wrong..??? Any idea's...!!??

*****************************************************************************************

After a reboot, sound started to work for any user. 

Worked out the video. Thought it must be a generic problem. Decided the reconfgure the xserver-xorg. 
For the modules  decided to add the two that where not loading in the original conf filen namely:
GLcore and v4l. 

Reloading the xserver and it all started to work. Wonder what those two do..??

**************************************************************************************

Actually I found that the problem is still there, in a way. Ubuntu is installed on a Dell D600. When I use the laptop display dvd's work. BUT when I use the port replicator and the external monitor, it stops working. 

I assume it is something to do with teh xserver, but have not idea what.

  :-?

---

### Post by phen on 2005-06-08
[QUOTE=department27]Hi I have a strange problem.

I have tried Totem, gxine and kaffeine, and they all give the same results. When I try to play a dvd or wmv, etc I get no sound or picture.

When I run any of the apps as sudo I get sound but no picture.

Have all the latest software, libdvdcss, etc.

What is going wrong..??? Any idea's...!!??

*****************************************************************************************

After a reboot, sound started to work for any user. 

Worked out the video. Thought it must be a generic problem. Decided the reconfgure the xserver-xorg. 
For the modules  decided to add the two that where not loading in the original conf filen namely:
GLcore and v4l. 

Reloading the xserver and it all started to work. Wonder what those two do..??

**************************************************************************************

Actually I found that the problem is still there, in a way. Ubuntu is installed on a Dell D600. When I use the laptop display dvd's work. BUT when I use the port replicator and the external monitor, it stops working. 

I assume it is something to do with teh xserver, but have not idea what.

  :-?[/QUOTE]
 got the same problem. DVDs won't playback. They do playback sound, but no video. On my internal laptop screen everything is fine. 

Strange, because mpegs and divx and other video file formats work without problems on my external monitor!

thanks for help!

kai

---

### Post by department27 on 2005-06-08
hi kai

Have a look at this thread. That fixed my problem.

[http://www.ubuntuforums.org/showthread.php?t=25668](http://www.ubuntuforums.org/showthread.php?t=25668)

Pete

---

### Post by department27 on 2005-06-11
Hi Kai,

Forgot to mention one more thing. You have to open up the xine gui and go to settings. Then go to setup and then audio. Change the default which I think is set to auto to xshm. Once that is set you will find that you should be able to what movies, etc in totem and xine.

Pete

---

