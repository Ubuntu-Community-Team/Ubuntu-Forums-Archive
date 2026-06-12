---
title: "Loading 9.04 on Dell Inspiron 2650"
date: 2009-06-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zincnlead on 2009-06-07
I am new to Ubuntu. Loaded it on a desktop ok, but having trouble getting to first base on my old Dell Inspiron 2650 laptop.
Booting the laptop from a CD Rom and running the installation from the CD I select Install, but end up with a blank screen with a "_" flashing in the top left hand corner. Is this an easy fix? I have 256MB Ram on this laptop.  
Appreciate any suggestions.

---

### Post by ugm6hr on 2009-06-08
> **zincnlead said:**
> I have 256MB Ram on this laptop. 

You will struglle with the LiveCD on just 256MB RAM; I would recommend using the AlternateCD, or use a lighter Linux distro (e.g. Puppy Linux) to create a swap partition, and then try again.

It is possible there is some other problem (e.g. corrupt install CD etc), since it is unusual to be left with a flashing cursor due to lack of RAM; normally you get left with a partially functional desktop.

---

### Post by nipponese on 2009-07-12
> **zincnlead said:**
> I am new to Ubuntu. Loaded it on a desktop ok, but having trouble getting to first base on my old Dell Inspiron 2650 laptop.
Booting the laptop from a CD Rom and running the installation from the CD I select Install, but end up with a blank screen with a "_" flashing in the top left hand corner. Is this an easy fix? I have 256MB Ram on this laptop.  
Appreciate any suggestions.

I ran into this problem yesterday. The solution is to turn off acpi.

From the cd boot UI: F6 (Other Options) -> x acpi=off

Then install as normal.

---

### Post by GhostDawg on 2009-07-18
zincnlead, did turning off acpi work for you? I'm having same issues with a few different distros also. I haven't tried 9.04 but downloading it.

Thnx.

---

### Post by afrodeity on 2010-02-16
acpi=off works fine for me.

[http://ubuntuforums.org/showthread.php?t=1348427](http://ubuntuforums.org/showthread.php?t=1348427)

---

### Post by afrodeity on 2010-02-17
Only downside is hibernate mode won't work without acpi, so I am appealing to the community to find some means of providing acpi support for these machines via a ppa as we move forward. Perhaps it is time to inaugurate the Dell Inspiron 2650 Ubuntu users club?

---

### Post by AKADriver on 2010-03-19
The problem with this laptop is that it only partially supports ACPI. This is a common issue with pretty much any flavor of linux on it.

[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

It needs the "pci=noacpi" option added to /boot/grub/menu.lst. Once you do that, you get all the power management stuff, battery life indicator, auto-shutdown, etc.

The only annoying part is that every time you grab a kernel update, you need to go back and add the boot option again - it defaults the new kernel to acpi=off.

---

### Post by afrodeity on 2010-03-19
I've got acpi=off, I take it, pci=noacpi replaces it?

---

### Post by afrodeity on 2010-03-19
Thanksk works like a charm. For karmic users, you need to edit  /etc/default/grub and then update-grub. This should be easier with kernal updates.

---

### Post by afrodeity on 2010-03-21
Just noticed my keyboard is now all crazy and can't reset with dpkg-reconfigure because there is no - (dash) available, blast. I'm tempted to simply go back to acpi=off which is easy to deal with, since at least I can edit grub file on another machine (no =)

---

### Post by afrodeity on 2010-03-22
Just realised dpkg-reconfigure is deprecated in Karmic. Oh dear, I need to take a look at a working xorg.conf file. Anbody have Karmic running properly on an Inspiron? Please upload your xorg.conf file.

---

### Post by rdunton on 2010-04-09
I too am having a same or similar problem.  I used the WUBI installer to try Ubuntu 9.10 on my Dell Inspiron 2650.  I had a screen with a blinking cursor under the following two lines:

[Linux-bzImage, setup=0x3400, size=0x3b26e0]
[Initrd, addr=0x177e8000, size=0x78bed2]

The screen before that says boot up with other options.  I selected ACPI workaround and it continued and installed Ubuntu.  After it completed installation, it restarted.  I was left with a boot menu showing:

Windows XP Home Edition
Ubuntu

when I selected Ubuntu, it went to grub2 and when I selected Ubuntu from there, it isn't booting correctly now.  I am getting the same problem that I had before I used the ACPI workaround.

How do I get the ACPI workaround now that Ubuntu is installed?

---

### Post by rdunton on 2010-04-09
If the OP hasn't found an answer yet, I may have a solution that will work for you too.  I also have a Dell Inspiron 2650, but I am running Ubuntu 9.10.  I tried this on my laptop and it works great.  If you haven't got it to install, when it goes to the screen that says use other boot options, select ACPI workaround.  From there, it should boot into and continue the install of Ubuntu.

After this, I was having a problem booting Ubuntu, getting the same or similar error again.  On Grub2, you have to select the first Ubuntu kernel, press 'e', and then add acpi=off to the line that starts with linux.  After quiet splash, type acpi=off.  This should get your laptop into Ubuntu.

Once you are in Ubuntu, you will have to edit /etc/default/grub.  You can do this in a terminal with the command:

sudo gedit /etc/default/grub

This should bring up the grub configuration file where you will see a line that says

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" (At least, that is what it was on mine)

If you change change it to "quiet splash acpi=off", this should allow Ubuntu to boot up correctly.

After you make that change, be sure to save the file and on the open terminal, use the command sudo update-grub.

Good luck!  Hope this works for you.

---

### Post by afrodeity on 2010-04-09
Was just about to say edit /etc/default/grub, but you beat me.

I think you only have to edit GRUB_CMDLINE_LINUX="acpi=off"

---

### Post by afrodeity on 2010-04-15
i need somebody with a working 2650 setup to dump their keymap into a file for me so that i can remap my keys which have gone totally awol>
see [http://manpages.ubuntu.com/manpages/...umpkeys.1.html](http://manpages.ubuntu.com/manpages/...umpkeys.1.html)

my keymap is completey kludged and i need to restore it and remap keys using a working keymap

thanks

---

### Post by afrodeity on 2010-04-16
i've created an ubuntu 2650 group for discussion and support issues related to the Dell Inspiron 2650 and Ubuntu

mailto:ubuntu2650laptop@googlegroups.com

---

### Post by soixante4 on 2012-01-09
Hello,
i just dig out my old 2650 and install linux mint Xcfe on it (xubuntu in fact).
I had problems with keyboard/touchpad non functionning if battery was connected.
I read many forums and all talked about "acpi=off" or "nolapic" or "noacpi".
The only one that solved the pb was "noacpi" but you all have to know that this option disables the management of the battery on the pc!!! It means you cannot know the battery level and so on!
For me the miracle came with the option "pci=noacpi" option which solve the pb but keep the management of the battery.
Hope this help!

---

