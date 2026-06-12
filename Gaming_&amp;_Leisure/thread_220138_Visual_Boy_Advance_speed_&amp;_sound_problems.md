---
title: "Visual Boy Advance speed &amp; sound problems"
date: 2006-07-21
forum: Gaming &amp; Leisure
---

### Post by aicrono on 2006-07-21
A friend and I are having a few problems with Visual Boy Advance and gvba.

Upon loading something, the framerate is getting around 250% and higher of the original intended speed of the game.

We have tried using the 'throttle' option and setting it to 100%, but the sound gets slowed down incredibly and the quality is horrible and the frame rate seems to be normal but a bit choppy. We have also tried fiddling with the frame skip options but it didn't even touch the high frame rate.

Anyone else experiencing this problem and/or have a fix to it?

We are both using Dapper if that is relevant to anything.

---

### Post by XVampireX on 2006-07-21
It seems I have had the exact same problem. My problem was that I used a tutorial once upon a time which was supposed to allow several applications to use alsa... But that turned out buggy and since alsa already does dmix by default, I removed the configurations of the file. The file is: /etc/asound.conf

If this is not the case, you might want to try and kill esd.

Alternatively, compile mednafen: [http://mednafen.com/](http://mednafen.com/)
Mednafen uses OpenGL for rendering. And in Castlevania: Aria of Sorrow, everything is seamless. Even going from one screen to another. VERY good emulator. Also, the OSD (On-screen-display) is very good. Make sure to press F3 to configure the buttons. and make sure to enable full screen by default in /home/user/.mednafen/mednafen.cfg file
Sorry, mednafen doesn't have a GUI, so you will have to launch the games through the terminal.

---

### Post by aicrono on 2006-07-21
Thank you very much! We went ahead and just tried mednafen and we both have it running with out a single problem! No GUI isn't really a problem for me at all. :D

---

### Post by DoktorSeven on 2006-07-22
Ah, nice.  Thanks for the pointer to Mednafen!

---

### Post by Diogo90 on 2009-05-10
Does it have a GUI or some kind of graphical interface?

---

### Post by disturbedite on 2009-05-10
VBA is dead and has been for a long time. i recommend VBA-M. it has continued development of VBA.

[http://vba-m.ngemu.com/](http://vba-m.ngemu.com/)

---

### Post by fabioxxxx on 2009-06-14
the sound for vba in linux sucked , wine with visualboyadvance 1.7.* 1.8 freezes a lot ...
but iv got realy happy with wine and no$gba 2.6   , perfect sound, resize the window(work only with gba not ds), save snapshots , no crash or freezing .

---

