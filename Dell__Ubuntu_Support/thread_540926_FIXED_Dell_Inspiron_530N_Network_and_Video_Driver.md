---
title: "FIXED: Dell Inspiron 530N Network and Video Driver"
date: 2007-09-02
forum: Dell  Ubuntu Support
---

### Post by rcdegges on 2007-09-02
Hi everyone. A few weeks ago I purchased a Dell Inspiron 530N desktop computer. Upon receiving it, I formatted it, and decided to reinstall ubuntu fresh. During the installation, I discovered that the network driver and the video driver don't work by default. This is especially annoying because you cannot connect to a network at all without a network driver.

I searched around for a while and found out a good fix for the problem. Finally, I got it working totally right, and want to share this information with the community. I wrote a nice little shell script to automatically install the video card drivers for all linux nVidia cards (32bit) and the ethernet driver (e1000). 

It is a very simple program to run and use. Simply download the file here:

[http://www.projectb14ck.org/files/code/shell_scripts/networkvideo.tar.gz](http://www.projectb14ck.org/files/code/shell_scripts/networkvideo.tar.gz)

then type the following commands into a terminal:

tar zxf networkvideo.tar.gz
cd networkvideo
./install.sh

Then follow the onscreen prompts. And when asked during the nVidia driver installation, don't forget to tell it to automatically configure your Xorg file so that you can get the most out of your new driver!

The only problem with this program's use is that if you update the kernel, you will need to rerun the program (or install the drivers by yourself again) because they are not auto detected by the kernel. 

Anyway, this program will solve your problems for the Inspiron 530N desktop, but will also work on any computer which has an e1000 based ethernet card and/or a nVidia video card. It will also fix any resolution problems you may be having.

So... Enjoy... If you have any questions or suggestions respond to the post and I will be more than happy to help.

-Randall

---

### Post by gbrainin on 2007-09-02
That's quite handy.  Of course, you have to have a working network connection to download your script. I guess I should burn this to a CD now before I need it.  : - )

---

### Post by rcdegges on 2007-09-03
Well, I would suggest putting it onto a flash drive. That way, the next time you can't boot up into X after an update, you simply log into the terminal without gdm, mount the flash drive, run my program, then reboot.

Doing that will correct your problem until the next kernel upgrade! I find flash drives much more convenient than cd's!

---

### Post by satbunny on 2007-11-23
If you should need to reinstall Ubuntu on a Dell Inspiron 530n desktop (and possibly other PCs) you should use the reinstall option in the GRUB menu at boot up [[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/OS_Reinstallation]](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/OS_Reinstallation]). If, however, you have repartitioned the disk and no longer have the reinstallation partition then you may try and use a Ubuntu install disk (you get one with the PC) or one you have downloaded or been given. You may even want to boot from a disk for another Linux distribution or one of the utilities that use the same boot kernel in what is called a LiveCD.

If you do you will be offered a menu, make a choice (install Ubuntu in this case) and may experience a very slow and eventually failed boot up. The screen may then drop to a simple text screen and error messages like this may appear:

    /bin/sh: can't access tty; job control turned off

    (initramfs) 34.324022 ata1.00 failed to set xfermode (err_mask=0x40) 



If so then you need to turn off your PC, start again and when you get to the first menu you need to add an option to the boot command line. On an Ubuntu install disk you do this by pressing F6 and adding the word irqpoll at the end of the line that appears. You then can press enter and it will install.

I learnt this from these posts on Ubuntuforums:


[http://ubuntuforums.org/showthread.php?t=417181](http://ubuntuforums.org/showthread.php?t=417181)
and
[http://ubuntuforums.org/showthread.php?t=578726](http://ubuntuforums.org/showthread.php?t=578726)

That explains how to get around the xfermode problem

BUT if you install from the 7.04 disk that is in the box with the PC then you will not have the right network drivers and no network capability.

Read here:

[http://preview.tinyurl.com/2dv3hs](http://preview.tinyurl.com/2dv3hs)

To that end you need to download the remastered Dell 7.04 disk from here:

[http://preview.tinyurl.com/2n6ooq](http://preview.tinyurl.com/2n6ooq)

Which has the updated drivers, although it also has OpenOffice removed, so you will need to then add that by using Synaptic from the System menu.

I then suggest that (as root) you ensure that the installed system is not prone to the same problem (which I did find it often was) by adding "irqpoll" onto the end of the grub boot line in /boot/grub/menu.lst

Ah well, early days, it's no more arcane than many Windows problems over the years! Don't let it discourage you getting a Dell Linux box, it will only be a short while before this is fixed..

I would not, however, commit to an upgrade to Gutsy online and certainly not using a standard Ubuntu install CD unless you are comfortable with the above and/or a Dell remastered install CD for Gutsy appears here:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

---

### Post by gbrainin on 2007-11-23
Thanks, satbunny, for an excellent, clear, and well-sourced solution to this problem!

One thing I noticed while skimming your sources is that the people who had this problem all seemed to have the CDRW drive in their computers.  This probably explains why I did _not_ experience this problem either with the standard 7.04 CD, the Dell modified 7.04 CD, or the standard 7.10 CD: both of the 530s I have have only the CD/DVD+-RW drive.

---

### Post by satbunny on 2007-11-23
I have a DVD RW drive, so I guess it's not just a CD RW drive issue.

---

### Post by gbrainin on 2007-11-23
Well, so much for that theory.  I guess I should just count myself as lucky, then.

---

