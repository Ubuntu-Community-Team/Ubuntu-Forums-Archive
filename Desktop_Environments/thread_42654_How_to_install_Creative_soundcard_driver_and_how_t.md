---
title: "How to install Creative soundcard driver and how to execute bin- and rpm-files"
date: 2005-06-18
forum: Desktop Environments
---

### Post by znuggle on 2005-06-18
**Hi outthere!**

I am the biggest newbie of all when it comes to Linux. I just installed Kubuntu 5.04 as a second OS (I still have Windows XP installed on another harddrive which works absolutely fine with everything) yesterday. I have been searching at Google to find out everything I can about Kubuntu.

What I've foung is how to install the newest nVidia graphics driver and to set my screen resolution right by editing /etc/X11/xorg.conf. I've done that and it's all working fine. I only have two issues left now:

-------------------------

**1) How do I install my soundcard driver?**
I have a Creative SoundBlaster Audigy 2 ZS soundcard which I need some drivers for. I don't know if Linux actually knows that I have a soundcard - it just make sounds from the motherboard when I make a mistake.

I have found these opensource Creative drivers ([http://sourceforge.net/project/showfiles.php?group_id=44773&package_id=37347](http://sourceforge.net/project/showfiles.php?group_id=44773&package_id=37347) ) but I don't know how to install them.
[U]
My system has following specs:[/U]
SiS Motherboard P4S5A/DX+
Intel Pentium 4 CPU 2.40 GHz
Kingston RAM 1024 MB DDR

nVidia GeForce 4 Ti4200 GFX
Creative SoundBlaster Audigy 2 ZS SFX

1 x Maxtor 80 GB HDD (Windows XP)
1 x Seagate 80 GB HDD (Kubuntu 5.04)

I use GRUB as bootmanager.

I hope you have some tips for me (please step-to-step it for me) - I really want to hear music in Linux :-)

-------------------------

**2) How do I excute an bin- or rpm-file?**
I'm having trouble execute files of the type .bin or .rpm. How do I execute those?

-------------------------

I hope you can help me. Thank you!

---

### Post by hammett111 on 2005-06-18
Okay let me tell you that in Kubuntu the drivers for the Creative Audigy 2 ZS (I have this soundcard by the way too - with the front panel) are already included. To activate your sound, this is what you should do.

1. Open your terminal (Konsole)
2. Type Alsamixer
3. Using your up down keys push all the speaker setups to almost full.
4. When you get to Audigy Analog/Digital output jack use the 'm" button on your keyboard to turn it on.
5. Push escape, close terminal and WALLAH!!!!!!!!! sound

Kapesh
Need a hand I'll monitor you thread

---

### Post by znuggle on 2005-06-19
Okay, I get in to the alsamixer but it says that I use the soundcard of the motherboard. I would like to use my Audigy 2 ZS.

How do I change this?

-------------------------

_Update:_

The onboard sound is working fine. I just want my 7.1 system to work. I still can seem to change the sound device. Do you have any idea of what I should do?

-------------------------

_Update 2:_

When I open KMix I can choose Audigy 2 ZS from the dropdown menu but I still can't seem to get any sound out of the speakers but the one from the onboard.

---

### Post by Mr.Clark on 2005-06-21
Have you tried disabling the on-board sound in the BIOS?

---

