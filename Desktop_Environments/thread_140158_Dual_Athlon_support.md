---
title: "Dual Athlon support?"
date: 2006-03-05
forum: Desktop Environments
---

### Post by MrDan on 2006-03-05
I really like the way ubuntu works on my computer and it does well on my other box (AMD athlon MP 2400 2ghz with 1 gb ram and Nvidia 256 MB DDR video card.)  I notice that while some other distros will show (and I assume use) both processors, the Ubuntu (edubuntu) does not.  Is there a way to get Ubuntu to utilize both processors?   

Also, is there a kind-of Cheat sheet of common commands so I could more effectively use the command line?  I do have a few books but is there something more condensed that I could carry in my pocket till I have them down?

Side note or bunny trail.
I am one of those guys who is really familiar with the "Other" operating system and really didn't much care for linux because it kept really messing up my other OS and I kept having to totally reformat my hd and start over.   (and over. . .)  I decided that I would give it a try again and this time using the whole HD and system and the whole shebang.   I was first impressed by the whole concept of the "live cd" and then how cool the OS really is once you get to know it.  I started out using the KDE but soon discovered the Gnome desktop.  Ubuntu so far seemed to be the only one that has Email that will check my work email (MS exchange server) which I fould to be pretty nifty.   Now I am actually considering making the "switch" once I find the perfect Distro (Or close to it).   Good work Linux)

Dan

---

### Post by procras on 2006-03-05
If you have more than one processor then you need to install the SMP kernel.

Beware that some things that work on the non SMP kernel will not work with the SMP one.

---

### Post by localzuk on 2006-03-05
Hi, To answer the first one, you need to install a 'smp' kernel via synaptic (or adept in kde).

---

### Post by MrDan on 2006-03-05
Thanks!

Although the Baware does raise some concern.   But I will try it out. :)

---

### Post by Sutekh on 2006-03-05
[QUOTE=procras]
Beware that some things that work on the non SMP kernel will not work with the SMP one.[/QUOTE]
Such as?

---

### Post by MrDan on 2006-03-05
well, I tried and now when I try to boot into it I get a login prompt that comes and ges about twice then I get a kind of crashy blue screen telling me that "failed to start the X server(your graphical interface).  It is likely that it is not set up correctly."

then another

"the X server is now disabled. restart GDM when it is configured correctly.


How do I Configure it?  What do I need to run or do or edit?

Oh the system in question is:
AMD athlon MP 2400 2ghz
Tyan tiger MoBoard
1 gb ram
Nvidia 256 MB DDR video card


When I get through the blue screens I get to Ubuntu Login but can't start GDM or KDM or startx...

Help me:cry:

---

### Post by Sutekh on 2006-03-05
When you get past the blue screens do you get to a command line (black screen) like 
```
Ubuntu 5.10 "Breezy Badger" ubuntu tty1
ubuntu login:
```

Try this to stop the display manager
```
sudo /etc/init.d/gdm stop
```
Then reconfigure the X server
```
sudo dpkg-reconfigure xserver-xorg
```
For most of these options you can accept the default or suggested options.

When you are through
```
sudo /etc/init.d/gdm restart
```
*Hopefully* will bring the GDM back up and you can log in

What did you install before this happened?

---

### Post by MrDan on 2006-03-05
[QUOTE=Sutekh]

What did you install before this happened?[/QUOTE]

SMP

---

### Post by Sutekh on 2006-03-05
I actually meant the name of the package

Like **linux-k7-smp** or **linux-image-2.6.12-10-k7-smp**?

Did you have NVIDIA drivers installed *prior* to installing the smp kernel?

If you did then you must install the linux-restricted-modules for your kernel, which are included in the linux-* package but not in the linux-image-2.6.12-* package.

---

### Post by MrDan on 2006-03-06
Well now I've done it!  Nvidia was working just fine before i went and messed with putting SMP for dual processor.  Now The nvidia poo-poo wont work anymore.:( 

Took off all the SMP junk and now I have lost the nvidia stuff and can't get it back.  I guess I will have to re-install to straighten everyhting out.


That'll learn me;)

---

### Post by Sutekh on 2006-03-06
When I do the installation on my box, I start with the default 386 kernel and install the nvidia drivers.  When I install the SMP kernel (I have a dual core Athlon) all I have to do is install the linux-k7-smp package.  It includes the -restricted-modules pacakge that allows me to keep the NVIDIA drivers intact.

Alternatively you can install them following this guide (you may have already seen)

[Ubuntu Forums - HOWTO: Latest NVIDIA Drivers](http://ubuntuforums.org/showthread.php?t=75074)

You shouldn't need to re-install everything, its only the NVIDIA stuff thats messed up.

---

### Post by MrDan on 2006-03-06
Thanks! maybe I will try that before I hang my hat on the other box.

---

### Post by Sutekh on 2006-03-06
Give it a shot, there aren't many instances where a total re-install is neccessary.  In my experience Linux is pretty tidy.

Go for Method 1, if you want the Ubuntu repository drivers (v7667) and Method 2 for the latest drivers (v8178)

---

