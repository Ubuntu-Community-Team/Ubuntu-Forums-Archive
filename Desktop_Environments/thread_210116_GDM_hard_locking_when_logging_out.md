---
title: "GDM hard locking when logging out"
date: 2006-07-06
forum: Desktop Environments
---

### Post by jonboy99 on 2006-07-06
Am having a problem with the computer locking solid and needing a hard reset when logging out to the gdm screen.

Is never a problem when starting up, but when logging out to switch users the screen will often go white with some blue blocks on.  It will do something if i type in a username despite not being able to see what i've typed, but then the desktop is white and won't do anything without the reset.

It was originally an ubuntu dapper fresh install, then I installed kde-desktop and use kde almost exclusively now.  After installing kde, kdm was doing the same thing so i uninstalled it and use gdm, but seem to have the same problem.

The computer never locks otherwise, jsut when logging out so don't think is overheating or anything.

Have ati firegl drivers installed.

Are there any log files etc i could look at to try and find out what's going on?

Cheers
Jon

---

### Post by 3rdalbum on 2006-07-06
You're using the ATI proprietry driver in the linux-restricted-modules package, aren't you?

There's a bug in that particular version of the driver. If you go to the ATI website, download and install the latest version, your log-out/shut down/restart/virtual terminals will all work perfectly.

---

### Post by jonboy99 on 2006-07-06
Not sure, I used the instructions from this page:  (method 2)

[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

If I type fglrxinfo at the CLI I get:

jonboy99@xp24ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 PRO Generic
OpenGL version string: 2.0.5814 (8.25.18)


So i don't *think* it's the driver you're talking about.

Is there anyway I can temporarily use the default non openGL drivers in ubuntu just to check if it's that without installing the new drivers?


[edit]

Ok, I swapped out my xorg.conf for a version I saved from ages back, without the fgl references and that used the mesa driver, and it solved the problem.  However I then swapped back to the same version i'd just been using with all the crashes, and it still seems fixed!  

Weird, but at least if the problem comes back i'll know where to start looking.

---

