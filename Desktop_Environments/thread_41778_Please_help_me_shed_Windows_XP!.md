---
title: "Please help me shed Windows XP!"
date: 2005-06-14
forum: Desktop Environments
---

### Post by Donshyoku on 2005-06-14
Hey, everyone, this is a two part thread (don't say I didn't warn you!).

I figured the topic may grab a few of you out here, and it is true.  I have tried several versions of Linux, and Kubuntu once.  I have found Kubuntu to be my favorite thus far, but I have a few problems that prompted me delete it and reinstall WinXP.  Now, I want to move back, but I need help with two things before I can go.

1)  No sound.  I am running an Intel 915G motherboard with the infamous Azalia audio chip.  I hear that ALSA 1.0.9 added my chip and the even newer ones, 1.0.9a and 1.0.9b should have it too right?  So, how do I update it?  I am fairly new in terms of Linux installs, so I really need some help.  Can I apt-get it, or kynaptic it?  

2)  TV support.  I recently ordered a Compro VideoMate TV/PVR tuner.  It runs on the Phillips SAA7130 chipset which I hear works in most Linux tuner programs.  So, which program should I use... MythTV, Freevo, TVTime?  And what steps would I be looking at to get my TV up and running... not too hard for a newb I hope?

Thanks in advance!  Please help me or I am going to download something from MSN Music, DRM and all! :razz:

---

### Post by intangible on 2005-06-17
1. Make sure you have the appropriate linux headers installed for your kernel (probably linux-headers-386) and then **sudo apt-get install alsa-source** if it doesn't ask you configuration information, then do **sudo dpkg-reconfigure alsa-source**, you shouldn't need ISA or debugging, so say no to those, then select **azx** for your sound.
Read /usr/share/doc/alsa-source/README.Debian for more info.

2. I really like tvtime out of all the programs I've tried, it's the nicest, does just what I want.  If it doesn't work without any config, try **sudo modprobe saa7134** and then try it.  If that makes it work, just put saa7134 in /etc/modules to make the module load on startup.

---

