---
title: "Dead X"
date: 2005-06-27
forum: Desktop Environments
---

### Post by Quest-Master on 2005-06-27
I upgrade my kernel from 2.6.10-4-686 to 2.6.10-5-686, reboot and get a number of various errors throughout the startup process.

The first ones that pop somewhere in the boot up process read like so: /etc/rcS.d/(something here): Input/output error.

Then, in the same behavior, modprobe complains about the apm module.

Lastly, when GDM and/or KDM fail to start up, this error is returned.

X: Cannot stat /etc/X11/X (input/output error), aborting.

---

### Post by kassetra on 2005-06-27
[QUOTE=Quest-Master]I upgrade my kernel from 2.6.10-4-686 to 2.6.10-5-686, reboot and get a number of various errors throughout the startup process.

The first ones that pop somewhere in the boot up process read like so: /etc/rcS.d/(something here): Input/output error.

Then, in the same behavior, modprobe complains about the apm module.

Lastly, when GDM and/or KDM fail to start up, this error is returned.

X: Cannot stat /etc/X11/X (input/output error), aborting.[/QUOTE]

oi.  I had this problem at first too... I bet you've just *now* switched from xfree to xorg...

How did you upgrade to Hoary?  I'm assuming you did a smart upgrade with Synaptic, eh?
If you did, you may not have all of the xorg packages you need.  Make sure you have xorg-common and xserver-xorg installed - and that could be the whole problem you have right now... but if they both are installed...  most likley you're going to have to copy your xf86-config to a backup and then rename the current xf86-config to xorg.conf

---

### Post by Quest-Master on 2005-06-27
Well, both xorg-common and xserver-xorg are and have been installed since I've been on Hoary.

:\

---

### Post by Quest-Master on 2005-06-28
[QUOTE=Quest-Master]Well, both xorg-common and xserver-xorg are and have been installed since I've been on Hoary.

:\[/QUOTE]
 Tried reinstalling them as well, continuously returns the stat'ing X error. I have an Intel Integrated Graphics Extreme also, FYI.

---

### Post by Lunde on 2005-06-28
What's the output of your /var/log/xorg.log or xorg.0.log?

Did you try to reinstall your graphics driver?

Also maybe there are a more apropiate driver for your card:

Linux drivers for Intel Extreme Graphics
[http://www.opendrivers.com/driver/219915/intel-extreme-graphics-driver-20040607-linux-free-download.html](http://www.opendrivers.com/driver/219915/intel-extreme-graphics-driver-20040607-linux-free-download.html)

---

### Post by Quest-Master on 2005-06-28
[QUOTE=Lunde]What's the output of your /var/log/xorg.log or xorg.0.log?

Did you try to reinstall your graphics driver?

Also maybe there are a more apropiate driver for your card:

Linux drivers for Intel Extreme Graphics
[http://www.opendrivers.com/driver/219915/intel-extreme-graphics-driver-20040607-linux-free-download.html](http://www.opendrivers.com/driver/219915/intel-extreme-graphics-driver-20040607-linux-free-download.html)[/QUOTE]

XOrg log.. [http://deadbeefbabe.org/paste/988](http://deadbeefbabe.org/paste/988).. excuse its size. :P

Also, how do I reinstall the current graphics driver? I'll give the ones you linked to a shot.

---

### Post by Lunde on 2005-06-28
[QUOTE=Quest-Master]XOrg log.. [http://deadbeefbabe.org/paste/988](http://deadbeefbabe.org/paste/988).. excuse its size. :P

Also, how do I reinstall the current graphics driver? I'll give the ones you linked to a shot.[/QUOTE]
 You are now using the i810 driver, most messages in your log referes to this driver so I'm prety sure this is the problem.

Discription of the packet i810switch from synaptics
-------------------------------------------------------------------------------------------------------------
Enables/disables video output to CRT/LCD on i810 video hardware
i810switch enables/disables the output to the CRT display and LCD,
depending on the i810 graphics controller hardware. Such hardware is found
on some laptops (eg, Sony Vaios, some Dell models, etc). Chipsets also
supported include i855, i830, i845.

This package includes the i810rotate script, which toggles the output
between three states: LCD only, LCD + CRT, and CRT only.
---------------------------------------------------------------------------------------------------------------

Reinstall this driver: 

$ sudo apt-get remove i810switch
$ sudo apt-get install i810switch

---

### Post by Quest-Master on 2005-06-28
Hmm, it was never installed (i810switch), so I installed and ran it. Didn't do anything. 

sudo dpkg-reconfigure xserver-xorg doesn't work anymore either, since I was asked to remove xserver-xorg and to reinstall it. Can't reinstall it as it always returns the error about not being able to stat /etc/X11/X (input/output error).

Also, noticed some other errors while booting up. In addition to the "/etc/rcS.d/(something here): Input/output error." I earlier noted about it, but it actually completely reads like so:
"/etc/rcS.d/(something here): line 13: /etc/udev/udev.conf (input/output error)"

This is really not looking good. I can't afford a reinstall of Ubuntu at the moment either.. :(

---

### Post by Quest-Master on 2005-06-29
Bump.. I haven't been on Ubuntu for 2 days, and these 2 days of simply Windows are killing me. :(

---

### Post by Lunde on 2005-06-29
[QUOTE=Quest-Master]Bump.. I haven't been on Ubuntu for 2 days, and these 2 days of simply Windows are killing me. :([/QUOTE]
 OK! I'm really sorry, but I'm a bit lost here too.

Your situation is now, correct me if I'm wrong
1.) you are unable to install X
2.) you are now on 2.6.10-5-686
3.) you probably also have an option in Grub to boot with the old Kernel 2.6.10-4-686

OK. when you upgraded your kernel, did you also get the source / linux headers for the new kernel?

Can you boot your old kernel and install X? I suggest you do that if you can, then do a tar  backup before you continue.
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)
in your case now, you can in this backup exclude also your /home because you are not going to do any changes to your user files while getting your kernel in order.

---

### Post by sonny on 2005-06-29
Well here's an idea: Download a hoary cd image, burn it, and do a complete re-install of your system. I think that is the best and cleaner way to do an upgrade, I also had some problems when I upgraded, and that was the way I solved them, I'm more of a practical guy, don't like long answers if I can get a short one.

Of course, this is a choice if you HAVE your home directory in a PARTITION, wich is always recommended.

---

### Post by Quest-Master on 2005-06-29
[QUOTE=sonny]Well here's an idea: Download a hoary cd image, burn it, and do a complete re-install of your system. I think that is the best and cleaner way to do an upgrade, I also had some problems when I upgraded, and that was the way I solved them, I'm more of a practical guy, don't like long answers if I can get a short one.

Of course, this is a choice if you HAVE your home directory in a PARTITION, wich is always recommended.[/QUOTE]
 
The problem is that I have lots of anime and other customizations.. it's too much for a reinstall.. unless during a reinstall of Hoary I am able to keep my /home. Is that true?

> Your situation is now, correct me if I'm wrong
1.) you are unable to install X
2.) you are now on 2.6.10-5-686
3.) you probably also have an option in Grub to boot with the old Kernel 2.6.10-4-686

All of these are correct, in addition to more older kernels as well in GRUB for number 3.

> 
OK. when you upgraded your kernel, did you also get the source / linux headers for the new kernel?

Yes.

> 
Can you boot your old kernel and install X? I suggest you do that if you can, then do a tar backup before you continue.

Will give this a shot now. Also, Lunde, if you could get on IRC (#ubuntuforums), or perhaps we could speak on MSN or something, I think that might streamline things a bit. :)

EDIT: I cannot install xserver-xorg on the older kernel either.

---

### Post by sonny on 2005-06-29
You can keep your /home directory IF ITS IN A DIFFERENT PARTITION.

---

### Post by Lunde on 2005-06-29
[QUOTE=sonny]You can keep your /home directory IF ITS IN A DIFFERENT PARTITION.[/QUOTE]
 If you only have a seconary disk, partition or CD writer, it should not be a problem.. then just move a backup of your home dir to this disk / partition / CD / DVD

how's your disk setup?

---

### Post by Quest-Master on 2005-06-29
[QUOTE=Lunde]If you only have a seconary disk, partition or CD writer, it should not be a problem.. then just move a backup of your home dir to this disk / partition / CD / DVD

how's your disk setup?[/QUOTE]
 
Ack, I don't have enough disk space to do that right now.. I'd have to go out and buy a new hard drive.

---

### Post by Lunde on 2005-06-29
Did you manage to boot your old kernel?

---

### Post by Quest-Master on 2005-06-29
[QUOTE=Lunde]Did you manage to boot your old kernel?[/QUOTE]

Yes.. X still didn't start though and won't install either.

---

### Post by Lunde on 2005-06-29
How big is your /home?
How big is your swap partition?
How big is your total disk?
Do you run windows in dual boot? 
Do you have space to store the /home there?
How much memory do you have?

What I'm thinking is to maybe disable swap, if you have enough memory, then convert the swap partition to Fat32 and use it as a temporary storage or bridge to moving the files to your windows partition / disk.

I'm sorry this is happening to you, but I think the best is to do a fresh install. I've upgraded my kernel a coupple of times and never this has happend to me.

---

### Post by codejunkie on 2005-06-29
try removing the package ubuntu-desktop it is just a meta package that installs the default ubuntu packages remove the xserver packages that are conflicting then do sudo apt-get install ubuntu-desktop -f this will reinstall and fix the broken xserver packages and reinstall the default ubuntu desktop packages that may be broken also i've seen alot of issues with the intel extreme video drivers so try using the vesa drivers with```
 sudo dpkg-reconfigure xserver-xorg
``` and choosing vesa or ```
sudo nano /etc/X11/xorg.conf
``` find the section that says Driver "example" and replace "example" with "vesa" and restart.

---

### Post by Quest-Master on 2005-06-29
[QUOTE=codejunkie]try removing the package ubuntu-desktop it is just a meta package that installs the default ubuntu packages remove the xserver packages that are conflicting then do sudo apt-get install ubuntu-desktop -f this will reinstall and fix the broken xserver packages and reinstall the default ubuntu desktop packages that may be broken also i've seen alot of issues with the intel extreme video drivers so try using the vesa drivers with```
 sudo dpkg-reconfigure xserver-xorg
``` and choosing vesa or ```
sudo nano /etc/X11/xorg.conf
``` find the section that says Driver "example" and replace "example" with "vesa" and restart.[/QUOTE]

Thanks man.. I'm going to give this a try now. Everyone pray for me please. <3

> How big is your /home?
How big is your swap partition?
How big is your total disk?
Do you run windows in dual boot?
Do you have space to store the /home there?
How much memory do you have?

/home is a 5+ gigs.
Swap is 512MB.
Entire HD is 40GB.
I run Windows in dual-boot.
Only 3 gigs of space left there.
256MB of RAM.

---

### Post by sonny on 2005-06-29
[QUOTE=Quest-Master]/home is a 5+ gigs.
Swap is 512MB.
Entire HD is 40GB.
I run Windows in dual-boot.
Only 3 gigs of space left there.
256MB of RAM.[/QUOTE]
If your /home directory is a partition of 5 gigs, then just re-install and access the option to manage partitions yourself, make the changes in the other partitions, when you get to your home partition, tell it not to format the partition, and put the /home as your mounting point, that way you'll still keep your home partition.

---

### Post by Quest-Master on 2005-06-29
Ok, guys.

I did it. And for those who have this problem later, this is what I did. A complete purge and remove of all of the old kernels first. Now, this may seem a bit dangerous, but when you're stuck with a dead system like me and the next option is to reboot, it doesn't seem too bad.

Completely remove /etc/X11/X with a sudo rm -rf /etc/X11/X. You can try renaming it as a backup or such, but I continuously got Input/Output errors while using mv, or even rm without -rf.

Now, I'm back and rocking in Ubuntu. :D

---

### Post by Lunde on 2005-06-30
I really hope **codejunkie**'s solution works for you, does'nt seem like a nice job moving your 5gig around.

---

### Post by Quest-Master on 2005-06-30
[QUOTE=Lunde]I really hope **codejunkie**'s solution works for you, does'nt seem like a nice job moving your 5gig around.[/QUOTE]
 
lol, it didn't. I posted the solution right above your post. :P

---

### Post by Lunde on 2005-06-30
[QUOTE=Quest-Master]lol, it didn't. I posted the solution right above your post. :P[/QUOTE]
 Glad to hear it worked out for you..

---

