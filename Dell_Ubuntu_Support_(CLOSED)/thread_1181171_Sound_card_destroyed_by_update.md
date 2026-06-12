---
title: "Sound card destroyed by update"
date: 2009-06-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by meread on 2009-06-07
Hello,

I have posted the following message in the Installation and Updates forum as it seemed the right place but have just noticed this forum so will repeat the message here as I am using a Dell Ubuntu laptop

"Hello,

Far from being a knowledgeable computer/linux/ubuntu user (I just want a system that works) I just followed the invitation to get and install updates from the update manager. All went well (it seemed) but the volume control says I do not have a sound card installed. I have and it worked fine before the updates.

I get this message when right clicking on the volume control and selecting open volume control

"No volume control GStreamer plugins and/or devices found."

and of course I do not have any sound.

Does anyone know if there will be a fix for this real soon?  
I have looked in the package manager(?) and it says I have loads of G streamer stuff installed.


Using Dell laptop with 8.04 hardy
kernel Linux 2.6.24-24
Gnome 2.22.3

Thanks a lot"

Roy

---

### Post by ajgreeny on 2009-06-07
Do you know what the update that caused the problem might have been?  Have a look in synaptic, File > History for the date in question and see if you can get any idea from that.

I don't think your sound card has actually been destroyed at all, I suspect the problem is just an update that has changed something and the sound card driver needs reconfiguring in some way.

---

### Post by meread on 2009-06-07
Thanks for your interest.  I agree the use of the word "destroy" is not really the best choice, it just feels like it.

Anyway have had a look at the history and copy below the list

Commit Log for Sun Jun  7 19:53:33 2009


Upgraded the following packages:
acpid (1.0.4-5ubuntu9.1) to 1.0.4-5ubuntu9.3
apparmor (2.1+1075-0ubuntu9.1) to 2.1+1075-0ubuntu9.2
apparmor-utils (2.1+1075-0ubuntu9.1) to 2.1+1075-0ubuntu9.2
apport (0.108.2) to 0.108.4
apport-gtk (0.108.2) to 0.108.4
cron (3.0pl1-100ubuntu2) to 3.0pl1-100ubuntu2.1
cupsys (1.3.7-1ubuntu3.4) to 1.3.7-1ubuntu3.5
cupsys-bsd (1.3.7-1ubuntu3.4) to 1.3.7-1ubuntu3.5
cupsys-client (1.3.7-1ubuntu3.4) to 1.3.7-1ubuntu3.5
cupsys-common (1.3.7-1ubuntu3.4) to 1.3.7-1ubuntu3.5
firefox (3.0.9+nobinonly-0ubuntu0.8.04.1) to 3.0.10+nobinonly-0ubuntu0.8.04.1
firefox-3.0 (3.0.9+nobinonly-0ubuntu0.8.04.1) to 3.0.10+nobinonly-0ubuntu0.8.04.1
firefox-3.0-gnome-support (3.0.9+nobinonly-0ubuntu0.8.04.1) to 3.0.10+nobinonly-0ubuntu0.8.04.1
firefox-gnome-support (3.0.9+nobinonly-0ubuntu0.8.04.1) to 3.0.10+nobinonly-0ubuntu0.8.04.1
gnome-system-tools (2.22.0-0ubuntu9) to 2.22.0-0ubuntu10
libcupsimage2 (1.3.7-1ubuntu3.4) to 1.3.7-1ubuntu3.5
libcupsys2 (1.3.7-1ubuntu3.4) to 1.3.7-1ubuntu3.5
libfreetype6 (2.3.5-1ubuntu4.8.04.1) to 2.3.5-1ubuntu4.8.04.2
libpango1.0-0 (1.20.5-0ubuntu1) to 1.20.5-0ubuntu1.1
libpango1.0-common (1.20.5-0ubuntu1) to 1.20.5-0ubuntu1.1
libpurple0 (1:2.4.1-1ubuntu2.3) to 1:2.4.1-1ubuntu2.4
libwmf0.2-7 (0.2.8.4-6) to 0.2.8.4-6ubuntu0.8.04.1
linux-backports-modules-hardy (2.6.24.23.25) to 2.6.24.24.26
linux-backports-modules-hardy-generic (2.6.24.23.25) to 2.6.24.24.26
linux-generic (2.6.24.23.25) to 2.6.24.24.26
linux-headers-generic (2.6.24.23.25) to 2.6.24.24.26
linux-image-generic (2.6.24.23.25) to 2.6.24.24.26
linux-restricted-modules-common (2.6.24.16-23.56) to 2.6.24.17-24.1
linux-restricted-modules-generic (2.6.24.23.25) to 2.6.24.24.26
ntpdate (1:4.2.4p4+dfsg-3ubuntu2.1) to 1:4.2.4p4+dfsg-3ubuntu2.2
pidgin (1:2.4.1-1ubuntu2.3) to 1:2.4.1-1ubuntu2.4
pidgin-data (1:2.4.1-1ubuntu2.3) to 1:2.4.1-1ubuntu2.4
pm-utils (0.99.2-3ubuntu10) to 0.99.2-3ubuntu10.1
python-apport (0.108.2) to 0.108.4
python-problem-report (0.108.2) to 0.108.4
xulrunner-1.9 (1.9.0.9+nobinonly-0ubuntu0.8.04.1) to 1.9.0.10+nobinonly-0ubuntu0.8.04.1
xulrunner-1.9-gnome-support (1.9.0.9+nobinonly-0ubuntu0.8.04.1) to 1.9.0.10+nobinonly-0ubuntu0.8.04.1

Installed the following packages:
linux-backports-modules-2.6.24-24-generic (2.6.24-24.32)
linux-headers-2.6.24-24 (2.6.24-24.53)
linux-headers-2.6.24-24-generic (2.6.24-24.53)
linux-image-2.6.24-24-generic (2.6.24-24.53)
linux-restricted-modules-2.6.24-24-generic (2.6.24.17-24.1)
linux-ubuntu-modules-2.6.24-24-generic (2.6.24-24.39)


Nothing 'sound' obvious but then it is all a mystery to me.

I have a hunt round the menus and system stuff but nothing that seemed to apply

Roy

---

### Post by ajgreeny on 2009-06-07
I agree, but it may be that the new kernel has upset your sound driver in some way.  When you boot, if you gat more than one kernel showing in the grub menu, not counting the recovery mode, try the older one, probably third in the list after the recovery mode which is second, and that may still give you sound.  If so, just boot to that each time.  You may even want to uninstall the kernel causing you the problem, but be sure to pick the correct one, with all the correct version numbers.

This must be in an older version than 9.04, I think, but that should not make a big difference to the procedure.

---

### Post by meread on 2009-06-07
By gum! you got to be quick to catch the messages as the machine boots, my eyes are not what they were!

Anyway you were right.  Using the previous kernel version the sound card works, but not the wifi.  Never mind I might look in the network area to fix that and if it is not there no matter as it works in this (new kernel) configuration.  It is just that I like to listen to BBC podcasts when I am away and stuck in a hotel, so as I can boot up with sound now and again that is OK

So VERY MANY THANKS for your help.  

I hope a kernel fix comes along soon as this is not quite what I expected from Ubuntu but then as I can't write the code who am I to complain.

Cheers

Roy

---

### Post by ajgreeny on 2009-06-07
You may well find that ubuntu 9.04 is better with wifi than whatever version you are running, so it could be worth installing that, even on a new small partition to have a look.

Just for your interest, I run two hard disks, my main OS on a 160GB, Ubuntu 9.04 (and an old WinXP which I only use for my old scanner), and another 40GB divided into 2 x 20GB for testing other OSs.  It keeps me up to date with newer versions of OSs and lets me try before I do a final install on my main 160GB disk.

---

### Post by niteshifter on 2009-06-07
Hi,

This happens to me on every kernel upgrade. I follow the procedures given [here]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade"), starting
at the bottom section - "If already running 8.04 and upgrading ..."

---

### Post by meread on 2009-06-08
Thanks very much to niteshifter and ajgreeny your assistance much appreciated.

I followed the link to the "issues - no sound...." etc page and followed the instructions and hey presto! sound just in time for my hols.  Great.

On a serious note in case any else with the problem reads this - don't forget to change the 
2.6.24-17-generic bit to the version you have just upgraded to.

There is so much to learn with Linux, it is fun but much burning of midnight oil.

I have two Linux machines.  A desktop running KDE 9.04 which I installed myself on a bare bones bundle
and my Dell laptop.  I was tempted to buy a laptop without O/S and install
Linux myself but Dell was cheaper with Ubuntu on it so took the easy way out.

Cheers

Roy

---

