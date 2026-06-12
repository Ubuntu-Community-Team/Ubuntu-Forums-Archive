---
title: "Installing XUbuntu onto Intel Atom system"
date: 2012-04-02
forum: Desktop Environments
---

### Post by valsetz on 2012-04-02
I was given a Intel Atom Computer that was used at a school to give graphs on a monitor for the staff to see how their power consumption was for the day. Here is what I know about it:

Was originally a MVix system
The case is a small form factor style
1 gig of memory DDR2 800
Guessing that the mother board is a ZOTAC - this is based off of the fan on the CPU, also had a screen that it would get stuck on when messing around with installing Ubuntu earlier that said ZOTAC. Can not find any other info on the motherboard physically. 
HDD is a Western Digital 2.5" 150 gig

I want to install Xubuntu onto this computer. I plan on using it as a media center in my living room. The problem I am having is that you can not boot from the USB so I can not install Xubuntu while the HDD is installed in that physical computer. So I have removed the HDD and put it in another computer and installed Xubuntu 10.04 LTS. My concern is that the OS is setup to work with the temporary computer that I used to install it. Is there a way that I can install it with the HDD in the Atom system that way it is perfectly setup for it? There are spare SATA conncetions so maybe I could take a spare HDD from another system and try to use that one to install  the OS into the 2.5 inch one meant for the Atom system. Kind of a pain in a butt to do it this way so I was wondering if there was another way. Any help would be great. I did install Ubuntu 10.04LTS how I described above with the second computer and it worked a couple of boots but then would not boot anymore and so I am trying Xubuntu to see if this will work better.
Is there a program that I can use with Xubuntu to check to see what motherboard I have in the Atom system?
Any advice would be great.
I am new at linux all together so I will need some detailed help. I have been around computers for 20 years so I don't mind getting into them physically and changing HDD around. 
Thanks
Valsetz

---

### Post by BertN45 on 2012-04-02
You have to install the system using the Atom PC, otherwise most of your your drivers will be wrong and even the cpus might be incompatible.

What boot device does your system support? Sometimes during loading the BIOS, you can select a boot menu. Otherwise you have to enter the BIOS and look there for a possible boot device.

In general I would expect that the system would support some USB options, like as a minimum CD/DVD on USB. At least my old eeePC did.

If you do not have one, try to borrow one.

---

### Post by BertN45 on 2012-04-02
Otherwise try following:

[http://agnipulse.com/2011/08/install-ubuntu-hard-disk/](http://agnipulse.com/2011/08/install-ubuntu-hard-disk/) 
or
[http://blog.mypapit.net/2008/10/install-ubuntu-from-harddisk-without-cdrom.html](http://blog.mypapit.net/2008/10/install-ubuntu-from-harddisk-without-cdrom.html)

It describes how you can install from the hard disk itself.

---

