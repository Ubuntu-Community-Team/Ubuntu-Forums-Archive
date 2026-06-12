---
title: "create live cd from existing installation without installation disk"
date: 2008-12-22
forum: General Help
---

### Post by LordIshamael on 2008-12-22
hey i want to create a custom live cd with all my settings and everything, i checked on the net and it says that remastersys can do this but remastersys says at one point that it may require the installation disk
i dont have the installation disk with me now, besides which im now on 8.10 and the disk was for 8.04

is there any way i could use remastersys or maybe some other software to create a custom kubuntu live cd with which i could then, you know, reinstall or something if needed

---

### Post by eBoxNet on 2008-12-22
Check this tutorial : [http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

---

### Post by LordIshamael on 2008-12-23
i was hoping for something a little less complicated...
but thanks anyway!this should do the trick

---

### Post by Fragadelic on 2008-12-31
Remastersys will do what you want and hasn't needed the original cd since version 2.0 rolled out a long time ago.

[http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com)

I'm the author of remastersys.

---

### Post by LordIshamael on 2009-01-01
oh great then, what i saw was prob outdated
thanks a lot!

---

### Post by LordIshamael on 2009-01-03
ok i used remastersys, created the livecd, it boots up fine and everything
but it doesntlog into any of the desktop environments, doesnt even show the login prompt, just a blank black screen with a flashing cursor on top (no i cant type anything)
gnome, kde, xfce are on my comp, and all three choices are on the cd
if i use ctrl-alt-f[1-6] i get the cli, i start gdm (again, kdm doesnt work), this brings me to the login prompt
i can login, but only if i select kde as the session beforehand
anything else (leaving it default - thats if i dont change default to kde - starting gnome or starting xfce produce a blank ochre screen)

kde works fine, the installation options are working great there - not that ive actually tried installing, but i ran the first few steps of the setup wizard, and it seems to be working

but id much prefer to operate the livecd from xfce as its much faster, so any idea how to rectify this error?possibly on the current livev cd, if not then when making a new one?

---

### Post by Fragadelic on 2009-01-21
gdm is the default within casper and if it findss it, gdm will be the login manager for the livecd.  It will also use whatever is the default desktop.

You really have to set your system up with true system default settings as the individual user settings will only work for backup mode.

If you used dist mode, the system is just plain and resorts to whatever the system defaults are set to.

It is up to you to set these before you run the dist mode.

What I tell folks before they run dist is to create a new user and see if that is how you want it cause that is how the livecd user will be.  You can set some stuff up through /etc/skel which is the new user skeleton folder but you have to understand what it is that you want the new user to have and avoid stuff that is for a specific user.

If you go through the wiki's from my webpage, a lot of this is explained there already.

---

### Post by grndslm on 2009-06-26
> **eBoxNet said:**
> Check this tutorial : [http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

And check this one while you're at it...
[http://ubuntuforums.org/showthread.php?t=1073838](http://ubuntuforums.org/showthread.php?t=1073838)

---

### Post by unr-convert on 2010-03-04
I successfully ran the remaster (with the option of including my own files). When I tried to reinstall it on another (identical Acer) it failed with an error about not being able to create grub.
Would appreciate any help in resolving this.

---

