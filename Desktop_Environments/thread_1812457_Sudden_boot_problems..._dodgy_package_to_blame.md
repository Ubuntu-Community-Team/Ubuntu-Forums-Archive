---
title: "Sudden boot problems... dodgy package to blame?"
date: 2011-07-26
forum: Desktop Environments
---

### Post by curiousornge on 2011-07-26
Hi all,

My trusty 11.04 x64 Ubuntu desktop machine stopped booting up properly about 2 weeks ago - it goes through Grub and into Plymouth, but then freezes and stops responding to keyboard input either on a dark purple screen, or less often the same but with the Ubuntu logo and the 5 boot progress circles but with none of them lit up.

I can hit escape early on after grub and see initialisation reports showing everything successful (other than a fail on "Automatic crash report generation") - up to a line saying "Stopping System V runlevel compatibility [OK]", at which point it freezes.

Going into recovery mode allows me to fsck the disk (which is fine, and smartctl reports all attributes as fine), fix packages (which I have done a number of times, to no avail) and boot into safe graphical mode, which works fine, albeit only on one monitor and with very poor graphics performance, obviously.

As the machine was borked and everything was backed up on my fileserver anyway, I decided to nuke it and give Fedora a go (I've been using Ubuntu since Feisty and it was a good time to try something else).  Fedora was fine (and worked with the default nouveau driver), but I didn't like it, so after less than 24 hours away from the fold I decided to come back to Ubuntu.  At least a reinstall should fix the problem with booting, right?  Wrong!  The live CD worked fine, installed perfectly, and the machine behaved itself upon first reboot - at which point I ran apt-get dist-upgrade, restarted, and blam - right back where I started.  Updated vanilla Ubuntu 11.04 will not boot.

Has Ubuntu released a dodgy package that has broken my x server?  Help me figure out what is wrong!  I don't want to have to go back to 10.10 - I'm one of these strange people who actually like Unity!

The machine: Core i7 with an 8800GT, 12GB of DDR3 and an SSD.  Has run perfectly well on at least 4 previous versions of Ubuntu, all installed rather than upgraded, including both instances of 11.04.

Things I've tried so far (suggestions from [http://ubuntuforums.org/showthread.php?t=1800640](http://ubuntuforums.org/showthread.php?t=1800640) and elsewhere):

* swapped back and forth, a few times (from safe graphics mode), between the two available nVidia binaries "173" and "current", with reboots in-between, 
* automatically reconfigure the x server from the recovery menu
* "apt-get remove --purge gdm" followed by "apt-get install gdm"
* "add-apt-repository ppa:gdm2setup/gdm2setup" followed by "apt-get update" and "apt-get install python-gdm2setup", which did not work as this repository came back with 404
* tried adding "vmalloc=192M" to the kernel parameters in Grub
* tried adding "quiet nosplash" to the kernel parameters in Grub

---

### Post by Peter09 on 2011-07-26
Go into recovery mode and select - repair broken packages - see if that helps.

---

### Post by curiousornge on 2011-07-26
Have tried that, no such luck unfortunately.

I've seen people talking about similar problems and saying they downgraded their kernel and got rid of the problem.  I've tried running the kernel that came with 11.04 (2.38.8?) rather than current (2.38.10?) from grub as well, but that made no difference in this case.

Is it a particularly bad idea to attempt to go even further back (2.36.xx)?  How do you even go about doing that?  I've always trusted apt to get me packages that work, so I have no experience telling it to get me a specific version of anything.

---

