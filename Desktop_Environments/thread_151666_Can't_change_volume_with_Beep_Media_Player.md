---
title: "Can't change volume with Beep Media Player"
date: 2006-03-28
forum: Desktop Environments
---

### Post by chugru on 2006-03-28
Hi All...

I have BMP 0.9.7 installed and working, except...

The volume control bar won't adjust volume. At the extreme left, it stops sound output. Anywhere else along the slide bar, the sound is present, but doesn't change volume from low to high.

Any ideas what I may be missing??

Thanks!

---

### Post by danielph on 2006-03-28
I have the same problem also in Beep,  XMMS and GXINE. Totem works ok, Sid you get an answer??

cheers

Dan

---

### Post by mrjohnston on 2006-03-28
If you only have problems with Beep it should be an issue with your output source.  

You need to right click on the top section of Beep and select preferences.  

Then you can click the plugins text on the left hand side. 

Then select the last tab that says Output.

Change output to be ALSA

Sound control should work, but will affect sound in all applications, so you can click on preferences a ways below the ALSA selection box.  Then click on the checkbox for "Use software volume control".

Close out of the menu and enjoy your fully functional Beep install :)

---

### Post by danielph on 2006-03-28
Ah ha, this led me down the path to the problem. The Multimedia System Selector (System > Preferences > Multimedia System Selector) was configured to use OSS. Changed this to ALSA and then configured Beep as you suggested and Bob's your uncle - all works. Other apps followed suit. Now need to decide what to use. This looks interesting 
[http://listengnome.free.fr/]("http://listengnome.free.fr/")
 [http://ubuntuforums.org/showthread.php?t=126080&highlight=change+volume]("http://ubuntuforums.org/showthread.php?t=126080&highlight=change+volume")[http://listengnome.free.fr/](http://listengnome.free.fr/) 


thanks for your help dude

---

### Post by chugru on 2006-03-29
[QUOTE=mrjohnston]If you only have problems with Beep it should be an issue with your output source.  

You need to right click on the top section of Beep and select preferences.  

Then you can click the plugins text on the left hand side. 

Then select the last tab that says Output.

Change output to be ALSA

Sound control should work, but will affect sound in all applications, so you can click on preferences a ways below the ALSA selection box.  Then click on the checkbox for "Use software volume control".

Close out of the menu and enjoy your fully functional Beep install :)[/QUOTE]

Changing BEEP plugin from oss to alsa did the trick!

You're my best friend today!

Thanks... :D

---

