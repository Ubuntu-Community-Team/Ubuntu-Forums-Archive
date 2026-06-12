---
title: "Maverick on Dell M101Z"
date: 2010-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by echo59 on 2010-12-27
Hi,

I got a Dell M101Z for Christmas, pre-installed with Windows 7 64-bit, 4GB ram and 320GB HD.  It's got an AMD Athlon II K325 dual core processor.

It also comes with the option to run Ubuntu Light, which has been mentioned in previous threads.  I'm not sure if I want a restricted version of Ubuntu, so I have not installed this yet.

I've been trying to make a USB boot disk to try out Maverick on the laptop.  I've tried both the 64-bit and 32-bit versions using the Universal USB Installer 1.8.2.0 from pendrivelinux.com.  I used this pendrive on my previous laptop running lucid before I converted that laptop to a dual-boot Lucid.  I've it set up with a 2GB FAT partition and a 14GB EXT2 partition called casper-rw.  Following the advice on pendrivelinux, I have been using this partition for persistence, and have been creating the boot-stick by creating a 1GB casper-rw file and deleting it before running the 1st boot.  This worked fine for my previous laptop, but is not working now.

The boot sequence seems to be getting stuck at the "Checking Battery State" stage.  Occasionally I see the message:
> Init: rsyslog main process (2695) killed by ABRT signal
Init: rsyslog main process ended, respawning
I get this for message repeated for different numbers.

I've also tried using the Startup Disk Creator on my current Maverick laptop, using both the 32-bit and 64-bit .iso as my source and having a 1GB casper-rw which I deleted before booting.  No joy.

I'd appreciate any suggestions as to what I'm doing wrong!  Also, there's a recovery partition on the hard drive, which makes me slow to jump in and do a dual-boot using grub2.  What about if I let the Dell software install Ubuntu Light?  Can I change this to the desktop Maverick afterwards???

I'd appreciate any advice on the matter.
- Can I get the USB boot stick working
- Can I easily get a dual-boot system working here?
- Where does Ubuntu Light fit into all this?


-J

---

### Post by echo59 on 2010-12-27
UPDATE:
=======

I made another attempt using the instructions on [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar") using my 10.10 installation, including the modification detailed in the 1st comment.  I used a 32-bit .iso of Maverick.

This USB image booted on the 1st attempt.  I got the error messages:
> Unknown keyword in configuration file: GFXBOOT
Unknown keyword in configuration file: GFXBOOT-BACKGROUND
And also a significant pause at the BOOT: command before Maverick would boot.  Then it seemed to load OK.

I tried to install the proprietary drivers (wireless card & flgrx) but the installation wouldn't run.  I then re-booted and the next time it booted it went into what I guess is Ubuntu Light.  I know that the persistence worked OK, because a file I created on the desktop was visible when I booted from the USB onto my other laptop.  However, going back to the M101Z boots straight back to "Ubuntu Light" from the USB stick.

So it seems that the persistence file is working OK on the USB but the M101Z will boot into Ubuntu Light regardless.


-J

---

### Post by echo59 on 2011-01-02
Sorry, but I need to "bump" this at this stage.
J

---

### Post by alien878 on 2011-01-03
You probably already have unbuntu light installed.  In the windows system folder, click on ubuntu and select to chose which OS to boot at startup.  You can turn this off later if you want.

The downside is that this is a limited install and Dell have gone to great lengths to hide things.  A few hints I have found playing with it:

[LIST=1]
[*]You have to set the password to use sudo.  Boot into single user mode and you can set the password for your userID (search the forums for directions).
[*]There is no application menu and apparently, one cannot be added in unity (?!?!).  You can sort-of get around this by using the file browser to go to /usr/share/applications.  From there you can see and launch all the apps that aren't on the launcher.
[*]Once an app has been launched, it can be added to the launcher by clicking on the icon and selecting always show.
[/LIST]
I'm not sure what I think of this overall.  The big selling point is that it is "instant on".  However, people are soon going to realise it is only about 10s faster then windows coming out of hybernation (at least, it is for me).  A user friendly app manager might hook people before they realise this (and I'm not talking about the gnome package manager with its 1000's of cryptic package names).

EDIT: Oh, yeah.  You'll probably need to do a sudo apt-get update to see all the packages.  Otherwise, you will only see the installed packages.

---

### Post by echo59 on 2011-01-07
But does anyone have any ideas on the best way to go about installing 10.10 desktop?  In this scenario would want to remove Ubuntu Light altogether.

---

### Post by alien878 on 2011-01-07
I'm still trying to figure that out...

You might try apt-get install ubuntu-desktop.  I haven't had a chance to try it as the user config applet (to set the desktop) seems to be "crippled".

The "crippling" done in this distro is really annoying and unnecessary.  Ex.  If I change the language in /etc/defaults/locale, it magically reverts every once and a while.  What were they thinking?

I'm considering just re-installing.  However, the HW is so nicely set up in this install I'm reluctant start from scratch.  Also, I'm terrified of what is going to happen to the bootloader.  Who knows what cute surprises are awaiting me there.

---

### Post by alien878 on 2011-01-07
apt-get install ubuntu-desktop seems to have worked.  I had one package that wouldn't install.  I just commented out dell from /etc/apt/sources.list, apt-get update, installed that one package, restored sources.list, apt-get update and then I could finish the install.

I still haven't used it much, so I still have to see how stable it is....

---

### Post by echo59 on 2011-01-07
Seems to have fixed Lucid for me.  Thanks!!!

---

### Post by echo59 on 2011-01-07
Another question:- should I leave the Dell repository active or should I comment it out to disable it permently?

---

### Post by alien878 on 2011-01-08
I'm not sure what is best.  I left it in case there are some propietary drivers from dell in there.

---

### Post by echo59 on 2011-01-09
It seemed to go OK until I tried updating my packages.  Neither the Broadcom proprietary driver nor FGLRX updated correctly and I wasn't able to boot into Ubuntu anymore, except by going to single mode and selecting low-graphics.

I've tried every method I could find to try and fix these 2 drivers but nothing seems to work and I still can't boot.  So my next step is to try and go back to the start and try again.  Any suggestions as to how I could do that?

---

### Post by alien878 on 2011-01-10
In windows, there is a "Ubuntu light repair" item in the start menu.  I think it reverts the whole ubuntu install to it's original state.  I haven't tried it yet, but I probably will because ubuntu-desktop pulled in too many other things for my tastes.

---

### Post by alien878 on 2011-01-14
Just to update, the ubuntu light repair did indeed re-install ubuntu light from scratch as it was when the netbook was purchased.

I kinda like the unity interface.  But it is useless to me with only web/mail/skype.  It would be nice if there was better support for adding applications.

---

