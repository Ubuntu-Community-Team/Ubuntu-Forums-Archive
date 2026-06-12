---
title: "Xorg Troubles"
date: 2009-04-18
forum: General Help
---

### Post by aeuzent on 2009-04-18
Alright let me walk you through my problem, I installed Ubuntu for power pc on an old iMac G3. I've been using [this]("http://ubuntuforums.org/showthread.php?t=405934") guide to help me out. I ran right into the problem with xorg and reconfiguring the monitor settings to that it will run on the iMac's built-in monitor. So I did an alternate install of 8.04.1 for the powerpc and used apt-get to install xserver then reconfigured xorg.conf and got the system to display without any complaints. Over joyed I ran 'apt-get install ubuntu-desktop' and the machine finishes it's boot by going to standby mode. What happened is that somewhere in the desktop install something re-configured xorg.conf and now unable to put a picture on the monitor the Mac bios just sends the machine to standby. Ctrl-option-F1 does not kill x and wake the machine up so I'm kind of stuck doing a hard reboot that just leaves me in the same place when it finishes.

What I need to do is load the main partition with the new variables and re-edit xorg.conf with the correct values. I've tried using live-cd's without GUIs like the Ubuntu rescue disc and Finnix but I have problems mounting anything from /dev. What I can do is tell yaboot (grub for x86 users) to boot to "old" which boots the machine using the corrected xorg.conf and works great. But on a reboot I get standby mode again.

Be glad for any help I can get on this, it's driving me crazy.

---

### Post by Svensk023 on 2009-04-18
what does the screen display, if anything, while in standby mode?

---

### Post by aeuzent on 2009-04-18
The CRT clicks off, so no power. I've checked from my router and it looks like the board powers down too, no IP. 

So much for SSH

---

