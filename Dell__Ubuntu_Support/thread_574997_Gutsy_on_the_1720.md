---
title: "Gutsy on the 1720"
date: 2007-10-13
forum: Dell  Ubuntu Support
---

### Post by AndyQ on 2007-10-13
OK, Just upgraded to Gutsy (release candidate) on my 1720 and thought I'd start a thread to document my findings an dsolutions.

Don't upgrade to Gutsy from Fiesty using the upgrade-manager (at least not yet) as it got 3/4 of the way through and then aborted with some error (which unfortunately I can't remember as it was late last night). It did give me a suggested command to try to run but unfortuntely I thought I could remember it but of course by the time I started up a command prompt - I'd forgotten :(.

Anyway, tried a few things, eventually rebooted which actually worked BUT it booted to XFCE with no network, sound or stuff so I decided to install from scratch (thank God I took a backup first!).

The live cd worked straight off - booted up into Gutsy - network worked out of the box, no sound though. The install was easy and didn't take long. After the reboot, configured my network )just connect to the wireless router - no problem), went to the restricted driver section and selected the NVidia driver. This installed and then after a reboot all was well. Might still install the proper NVidia drivers at some point though. Still no sound though.

After a fair bit of searching, I came across this post ([http://ubuntuforums.org/showthread.php?p=3489580](http://ubuntuforums.org/showthread.php?p=3489580)) and decided to try the last solution on the first page :

sudo apt-get install module-assistant (useless cause you already have it if it's not the first time you do the trick)
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Also added the below line to /etc/modprobe.d/alsa-base (no idea if I needed to)
options snd-hda-intel model=3stack

After a reboot, I was greated by the welcome login sound and sounds is now working.

The touchpad works out of the box (including edge scrolling), but I still needed to add to /etc/X11/xorg.conf:
Option "SHMConfig" "on"

to enable synclient and to get circular scrolling to work.

Checked the webcam using Ekiga and needed to select V4L2 but it worked straight away.

Testing the internal mike - YAY it works out of the box!
Need to change a few settings - double click on sound control panel, select preferences from Edit menu and enable Digital Input Source.

Click OK and go to Recording tab, make sure that Digital is enabled and then click Options tab and set Digital Input Source to Digital Mic 1. Et Voila (test using Sound Recorder - select input as Digital).

Thats it so far, I'll update if I find anything else thats a bit odd. But so far, Gutsy has better support than Feisty for me.

---

### Post by dragonflyseven on 2007-10-13
Thanks for the information on the sound, I will try that in a second. I have a 1720 too, but my wireless is not working. Do you have the broadcom card? Besides sound and wireless, installation was painless for me too.

---

