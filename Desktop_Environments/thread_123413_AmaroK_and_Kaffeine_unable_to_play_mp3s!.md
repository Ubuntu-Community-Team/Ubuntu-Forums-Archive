---
title: "AmaroK and Kaffeine unable to play mp3s!"
date: 2006-01-30
forum: Desktop Environments
---

### Post by kinseikun on 2006-01-30
Hola once again.

Kaffeine said I did not have any win32 codecs...I downloaded the codecs and put them in the usr/lib/win32 folder. Then it said I had them, so I thought that meant I could play videos or mp3s. Wrong. Also, AmaroK will not play mp3s. XMMS will, but I've never liked WinAmp, so I don't really like it. Can someone help me out? (Please note I also cannot use apt-get, it won't update.)

---

### Post by RAOF on 2006-01-30
Why can't you use apt-get?  'Cause the easy solution to your problem is to run "sudo apt-get install gstreamer0.8-plugins*"

Let's try & fix apt-get.  You'll have a hard time installing anything in Ubuntu without it :)

---

### Post by DoorGunner on 2006-01-30
For Codecs follow the instructions in
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)
go to section 13 How to install Multimedia Codecs?

once you get your codecs installed correctly Xmms should work

amarok should be able to play your mp3/s....it just takes a little configing.
Go to settings>configure amarok>engine

ensure you have 
Gstreamer engine selected
Output plugin gconfaudiosink selected
click apply restart

you should be able to get it to work......


For Further help with Amarok try these
[http://amarok.kde.org/amarokwiki/index.php/MP3_on_Ubuntu_5.10](http://amarok.kde.org/amarokwiki/index.php/MP3_on_Ubuntu_5.10)
[http://www.ubuntuforums.org/showthread.php?t=75588&highlight=install+gstreamer-mad](http://www.ubuntuforums.org/showthread.php?t=75588&highlight=install+gstreamer-mad)
[http://amarok.kde.org/](http://amarok.kde.org/)

sorry not much experience with Kaffine

---

### Post by kinseikun on 2006-01-30
[QUOTE=RAOF]Why can't you use apt-get?  'Cause the easy solution to your problem is to run "sudo apt-get install gstreamer0.8-plugins*"

Let's try & fix apt-get.  You'll have a hard time installing anything in Ubuntu without it :)[/QUOTE]


:( Exactly! I made a thread here about my sad struggles with apt-get:
[http://www.ubuntuforums.org/showthread.php?t=123231](http://www.ubuntuforums.org/showthread.php?t=123231)

I hope you can help me!

Also, I did have the settings correct for Amarok, Gstreamer and gconfaudiosink selected and it still wouldn't play music after I restarted -_-.....

---

