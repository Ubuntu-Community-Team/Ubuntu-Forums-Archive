---
title: "Blank screen after grub - again"
date: 2015-06-28
forum: Desktop Environments
---

### Post by Jonners59 on 2015-06-28
I am having major, repeating problems on a number of machines all on the latest kernel/Ubuntu version, xfce and nvidia cards.

This machines
[COLOR=#000000]Running 15.04 64-bit[/COLOR]
[COLOR=#000000]linux: 3.19.0-21[/COLOR]
[COLOR=#000000]Intel Core i7-4820k CPU @3.70Ghz[/COLOR]
[COLOR=#000000]Nvidia GF108 GeForce GT430
[/COLOR]nvidi driver nvidia-352

[COLOR=#000000]This machine after GRUB has the black screen and cursor.  ctrl+alt+F1 or F2 does nothing and going in to recovery mode does not work either as no commands work even sudo shutdown -r now

[/COLOR]Any help please?

---

### Post by grahammechanical on 2015-06-28
I am not familiar with the age of those graphic adapters but I think that nvidia 352 is one of the latest nvidia drivers. From my experience with a nvidia GT 220 the latest nvidia drivers do not have support for some older nvidia adapters. Check the Nvidia web site to see what the recommend Linux driver is. We can also check the drivers to see what adapters they support.

Regards

---

### Post by Jonners59 on 2015-06-28
> **grahammechanical said:**
> I am not familiar with the age of those graphic adapters but I think that nvidia 352 is one of the latest nvidia drivers. From my experience with a nvidia GT 220 the latest nvidia drivers do not have support for some older nvidia adapters. Check the Nvidia web site to see what the recommend Linux driver is. We can also check the drivers to see what adapters they support.

Regards

It is the correct and latest driver.  It did work, but I find it unreliable.  Always end up by failing after a couple of uses....  Not limited to this driver, seems to have started with Ubuntu 14:10 and continued in to 15:04...

---

### Post by ajgreeny on 2015-06-28
Did you try the driver that is the default in **Additional Drivers**?

That may work far better than such a new one.

---

### Post by Jonners59 on 2015-06-28
> **ajgreeny said:**
> Did you try the driver that is the default in **Additional Drivers**?

That may work far better than such a new one.
Yes, that is where I started.....  Things started to go wrong for me and MANY others after 14:10 upgrade.  Seem to be a number of bugs out.  However, that is not my problem now.  I need and want to get this machine going.  So far after GRUB and the scripts it stops before the login screen.  However, I have managed to fix things in the past by ctrl+alt+F1 and installing the drivers, but it will not let me do anything.  ctrl+alt+F1 does not work and in Recovery mode none of the commands work.

Any ideas, please, anyone.

---

### Post by ajgreeny on 2015-06-28
Have you tried just using the open source nouveau driver?

I think I remember reading in a few places where nouveau was working very well with that card as long as it used the *nomodeset* boot option.

---

### Post by Jonners59 on 2015-06-28
> **ajgreeny said:**
> Have you tried just using the open source nouveau driver?

I think I remember reading in a few places where nouveau was working very well with that card as long as it used the *nomodeset* boot option.

Yes, but also nouveau does not have 3d rendering, it is just a basic driver...  That said it is still not the main issue, I can not add, purge or do anything as I can not login and ctrl+alt+F1 does not work.  I need to get access to the PC first....

---

### Post by Jonners59 on 2015-07-08
OK, I created a new install in parallel, as nothing worked and no one seems to know what is wrong.

I now want to move/copy my panels and desktop settings over to the new image so I do not have to start all over.

What has what......  that I can copy over??????

---

### Post by oldfred on 2015-07-08
All your user settings should be in /home. Only if you manually made system wide settings for hardware like your Ethernet card may some settings also be in /etc.

My backup is so I can document system and restore it easily.
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

Did you experiment with different nVidia drivers. If you do not completely purge one before installing another, you will have issues.

---

### Post by Jonners59 on 2015-07-10
Thanks OldFred, will review these... :-)

---

