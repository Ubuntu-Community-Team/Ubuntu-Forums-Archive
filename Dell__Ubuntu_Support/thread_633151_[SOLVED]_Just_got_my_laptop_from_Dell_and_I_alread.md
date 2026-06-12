---
title: "[SOLVED] Just got my laptop from Dell and I already crashed it..."
date: 2007-12-06
forum: Dell  Ubuntu Support
---

### Post by trooperchix on 2007-12-06
I am a total newbie to this, so commands and everything don't make a bit of sense, so please be patient.  I'm tired of giving my money to one of the richest men in the world, so here I am Ubuntu!!  

Ok, here's the scoop...  I just received my new Dell 1420N laptop with Feisty installed.  I tried to install independently Gnucash, and that failed.  I found elsewhere where I could add gnucash (through add programs) and that failed also.  I logged out, and attempted to log back in and now I get:

**The files that contain your preference settings are currently in use.  You might be logged into a session from another computer and the login session is using your preference settings files.  You can continue to use the current session, but this might cause temporary problems with the preference settings files.  You can continue to use the current session, but this might cause temporary problems with the preference settings in the other session.  Do you want to continue? **  and the option is log out or continue.  If I hit logout, I get back to the log in screen (and subsequently if I try to sign in again, I get the same edit) or, if I hit continue,  I get the following:

**Please contact your system administrator to resolve the following problem:  Could not resolve the address "xml:readonly:/etc/gconf/gconf.xml.mandatory" in the configuration file "/etc/gconf/2/path": Failed: Couldn't locate the backend module for 'xml:readonly:etc/gconf/gconf.xml.mandatory"**

I'm sure there is a wierd easy fix for this, basically as I understand it, the system thinks I'm logged into my profile already when I am not.  I can't wait until I get this down so I can ask more intelligent questions..  Your help would be much appreciated...

---

### Post by natehall on 2007-12-06
If you don't have any data you want to save you can do the factory reinstall. Just stop the boot up and follow the directions the BIOS gives you.

---

### Post by trooperchix on 2007-12-06
> **natehall said:**
> If you don't have any data you want to save you can do the factory reinstall. Just stop the boot up and follow the directions the BIOS gives you.

Ok, so I changed the boot sequence so it boots to the CD first so I can reinstall.  I hit the option to run/insall ubuntu from the disk, and I got:

/bin/sh: can't access tty; job control turned off
(initramfs) help
help

what now?

---

### Post by john_hull-DELL on 2007-12-06
If you're planning to reinstall feisty, your best bet is to use the reinstall process that's already on the hard drive. Info on how to do this is here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/OS_Reinstallation](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/OS_Reinstallation)

---

### Post by trooperchix on 2007-12-06
> **john_hull-DELL said:**
> If you're planning to reinstall feisty, your best bet is to use the reinstall process that's already on the hard drive. Info on how to do this is here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/OS_Reinstallation](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/OS_Reinstallation)

I have no idea how to "invoke GRUB" to do this...

---

### Post by trooperchix on 2007-12-06
Duh, figured it out.  Thanks man!!:)

---

### Post by PaJoe on 2007-12-06
trooperchix,

Sorry you are having so much trouble, linux can be frustrating to the new user that is accustomed to windows and having unlimited help everywhere.. 

I ended up in similar shoes, for different reasons. I think there is a problem with the Ubuntu  installation disk Dell included. Download the remastered cd image ( or dvd ) from Dell and run that installation program - it works well. At first it won't matter how many times you format and install it, but after a while you may have too much personal information to want to start over. 

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Dell_Remastered_Ubuntu_7.04_ISO](http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Dell_Remastered_Ubuntu_7.04_ISO)


after the fresh install try using "sudo apt-get install" whatever_program_you_ want_installed   

Hang in there and you will be OK


I

---

### Post by saru411 on 2007-12-06
> **PaJoe said:**
> trooperchix,

 At first it won't matter how many times you format and install it, but after a while you may have too much personal information to want to start over. 
I

i would recommend making a separate /home partition so that when you reinstall using the alt cd you can configure it to use your old /home partition. this will keep your files from being formatted every time you reinstall. this type of separating your /library folder works well in windows also.

---

### Post by trooperchix on 2007-12-07
Rock on guys, this worked fantastically.  Man, I get WAY better tech support response here than I EVER did in ANY fashion through Microsoft.  And why don't more people switch?  Windows Sux.
:guitar:

---

### Post by buntunub on 2007-12-07
Thats a weird issue you had. Its really very strange that Dell would ship your system in that kind of shape. It really should have been thoroughly tested prior to. Tsk tsk.

---

### Post by saru411 on 2007-12-08
> **buntunub said:**
> Thats a weird issue you had. Its really very strange that Dell would ship your system in that kind of shape. It really should have been thoroughly tested prior to. Tsk tsk.

if you would read the first post it seems to be from user error.

---

