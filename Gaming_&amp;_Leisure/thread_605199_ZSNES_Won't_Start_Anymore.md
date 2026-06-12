---
title: "ZSNES Won't Start Anymore"
date: 2007-11-06
forum: Gaming &amp; Leisure
---

### Post by mavsman4457 on 2007-11-06
I got ZSNES installed and running perfectly with fullspeed and my joystick working. I decided to set it to fullscreen because that looks the best but now when I open it up it gives me a full black screen like it is about to open and then just goes back to my desktop and doesn't open at all. How can I get this to run again and what did I do wrong?

---

### Post by dfreer on 2007-11-07
Try running it in the terminal, and post any output.

If nothing else, you can probably just backup your saved games and delete your ~/.zsnes/ folder, you'll lose all your settings, but that includes your bad video settings.

---

### Post by mavsman4457 on 2007-11-13
Thanks I will try deleting everything since I don't really have game saves on there.

---

### Post by mavsman4457 on 2007-11-13
OK I am sorry for the double post but this is just retarded.  I have tried uninstalling and reinstalling with the Add/Remove Program manager, I've tried marking ZSNES for uninstallation then installation in synaptic, and I even completely removed it in synaptic then reinstalled it using synaptic.  I also tried a 1.42 .deb install package and all of them gave me a flash of a black screen and then nothing when I tried to open ZSNES.  I really just want to delete all traces of ZSNES on my system and make it as though it were never there in the first place so I can install it now like I did the very first time.  Does anyone know how I can do this?  I just want to play ZSNES.  And I have tried snes9x and I don't like it.  ZSNES is far superior but at the moment and doesn't want to open up for me.  Anyone know how to fix this for me?

---

### Post by jondecker76 on 2007-11-13
as someone else said earlier, I would recommend deleting the .zsnes folder in your home directory - this will reset all of the settings

If you're not familiar, files starting with a . (period) are hidden. To see them, browse to your home folder in Nautilus and under the view menu click on View Hidden Files.. Then you will easily be able to delete the .zsnes folder.

---

### Post by disturbedite on 2007-11-13
> **mavsman4457 said:**
> I really just want to delete all traces of ZSNES on my system and make it as though it were never there in the first place so I can install it now like I did the very first time. 
that is precisely what remove with configuration/purge does with synaptic. 

[quote=mavsman4457]ZSNES is far superior but at the moment and doesn't want to open up for me.[/quote]
that is true, it is superior to snes9x as far as pure emulation is concerned.

but as far as your issue, i'm sorry, i really wish i could help you but i don't know what else to do that you haven't already...

except, maybe you could grab zsnes from svn & compile it yourself to see if the problem has been fixed.  (or whether its just a problem on your end of course).

---

### Post by nandotron on 2007-11-15
Hi guys,

I'm having this same problem with zsnes.  the output for zsnes in the terminal is:

```
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/enda/.kde/socket-enda-laptop.
can't create mcop directory
```

just wondering if you guys can offer any suggestions?

thanks!

---

### Post by dfreer on 2007-11-15
You can create the folder in question, there's several threads on here about how to do that. Or you can install my version of zsnes, which doesn't have this problem ;) *shameless plug*

---

### Post by TheodoreBSlambs on 2008-02-11
i have the exact same problem. even tried a different mouse, usb and ps2. i uninstalled zsnes thru sudo apt-get, then deleted the .zsnes folder. reinstalled it, and the same error comes up. any suggestions?

---

### Post by erginemr on 2008-02-12
Try installing the ZSnes debian package given in getdeb.net:
[http://www.getdeb.net/app/ZSNES](http://www.getdeb.net/app/ZSNES)

---

### Post by TheodoreBSlambs on 2008-02-13
that worked. but then it said there is a newer version available. so i did the sudo apt-get install zsnes, and it said it upgraded it. still works fine tho.

side note, just wanna say that i first installed ubuntu in october, dual booted with vista. and not that i dont like vista, but i have used ubuntu almost strictly since then. im trying to pass it on to friends and family.

---

### Post by couzin2000 on 2008-02-13
> **erginemr said:**
> Try installing the ZSnes debian package given in getdeb.net:
[http://www.getdeb.net/app/ZSNES](http://www.getdeb.net/app/ZSNES)

I tried installing the deb package, and it worked great -- not only that, but it was reading my ROM files from a NTFS partition without any glitches!

HOWEVER - I saw the same update notification. So I went and did it. I get back, and it doesn't start. I get a window taht opens and closes in a heartbeat.

This has something to do with the permissions to certain devices, and a permission to play around in a specific folder. What permissions should I set this to, and with what command? I'm assuming chmodding these should work, but there are options and I'm not familiar with them. Please take me through the steps, for the benefit of everyone.

---

### Post by erginemr on 2008-02-14
Don't worry. I will figure out a way to disable that nasty upgrade notification for zsnes...

---

### Post by kbless7 on 2008-02-14
As suggested by the output of the terminal you guys are getting a "mcop error" in zsnes. Fortunately it is very common. Here is a link of how to fix it.

[http://ubuntuforums.org/showthread.php?t=593888](http://ubuntuforums.org/showthread.php?t=593888)

-Matt

---

### Post by erginemr on 2008-02-14
If the above method does not work, you may follow this one:

1. Remove the ZSnes version installed by the update manager:
```
sudo aptitude remove zsnes
```

2. Reinstall the Debian package you have downloaded from getdeb.net by double-clicking on it. Disregard the "you should install software from the repositories" warning.

3. Take a copy of your dpkg database for extra safety:
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.mybackup
```

4. Edit the original file with:
```
gksudo gedit /var/lib/dpkg/status
```

5. Find the line "Package: zsnes". The corresponding block should be something like
```
Package: zsnes
Status: install ok installed
Priority: optional
Section: otherosfs
Installed-Size: 3368
Maintainer: Joshua Kwan <joshk@triplehelix.org>
Architecture: i386
Version: 1.510-1~getdeb1
Depends: libc6 (>= 2.5-0ubuntu1), libgcc1 (>= 1:4.1.2), libgl1-mesa | libgl1, libpng12-0 (>= 1.2.13-4), libsdl1.2debian (>= 1.2.10-1), libstdc++6 (>= 4.1.2), zlib1g (>= 1:1.2.1)
Description: Emulator of the Super Nintendo Entertainment System (TM)
 ZSNES allows you to play classic games written for the "SNES" game
 console on a GNU/Linux system. It supports advanced features such as
 multiplayer gameplay over a TCP/IP network.
 .
 Please note that many separately-available games playable under this
 emulator are non-free. See /usr/share/doc/zsnes/README.Debian for more
 information.
```

Replace the line "Version: 1.510-1~getdeb1" to say, "Version: 1.520". This way, we shall trick Synaptic into believing that the ZSnes version from getdeb.net is higher than the one available in the Ubuntu / Debian repositories.

6. Update your status with the new database:
```
sudo aptitude update
```

That is all there to it. The update manager will not bother you anymore until a new version comes out. 

This technique also works for any such bothersome packages other than zsnes.

---

### Post by disturbedite on 2008-02-14
or just don't update it.  is that hard to not update it?  ;)

---

### Post by MEGAMANULTIMATE on 2008-02-16
Hi, all. Just got done installing gutsy and everything seems to be in order except for zsnes. After I set the video, it stopped working. I tried playing around with the video with no luck. Here's the output of 'sudo zsnes':


matthew@matthew-laptop:~$ sudo zsnes
[sudo] password for matthew:
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: SynPS/2 Synaptics TouchPad
Mouse 1: Macintosh mouse button emulation
Creating link /root/.kde/socket-matthew-laptop.
can't create mcop directory

Any ideas? You'd have my undying gratitude.

---

### Post by MEGAMANULTIMATE on 2008-02-16
Never mind guys, I fixed it. I feel so stupid for posting that now...sorry!

---

