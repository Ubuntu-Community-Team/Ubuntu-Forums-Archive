---
title: "initramfs (busybox) error"
date: 2009-03-29
forum: General Help
---

### Post by stabf on 2009-03-29
I'm attempting an install of Ubuntu 8.1, the kind where you install it while running windows (since the boot time install was only allowing me to use half of my entire harddrive space to install it).

The windows portion of the installer works fine, but when I reboot and try to run Ubuntu, I only get as far as the splash screen. After going through and looking for solutions, nothing has helped.
If i disable the splash screen, it loads many lines of code, most of which say something like "attempting to read location out of range" or something to this effect, and then i get kicked to INITRAMFS.
I'm wondering if its attempting to load from something that i do not have (A floppy drive?) or something.

I'm running Windows XP, media center edition on a Dell XPS1730.
I have 2 200gb drives in RAID.

---

### Post by stabf on 2009-03-29
I have been attempting to fix this issue with fixes from this website for at least the last 2 hours. I'm seriously debating just saying "screw it" and labeling Ubuntu as a complete waste of time.

---

### Post by abn91c on 2009-03-29
try post the error message you getting, for starters type **exit** at the initramfs prompt to check if anything happens

---

### Post by linorics on 2009-03-29
If your using Wubi installer. I don't think you can install it that way with Raid. 

"Software raid arrays 0 and 1 are not supported."
Link --> [[COLOR="DeepSkyBlue"]Wubi Wiki[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#Software%20raid%20arrays")


Try installing on an external drive as a test.

---

### Post by stabf on 2009-03-29
Ok, so I'll buy that i can't Wubi install because of my raid, but what about just a regular boot install? when i get to the partition manager, it doesn't say that I have any partitions of any size, and If i try to do any other option, it tries to make me use an entire one of my two drives as Ubuntu's install space. I don't think i really want to give Ubuntu 200 Gigs, and lose anything that might be on that drive.

---

### Post by stabf on 2009-03-29
Oh and when i type exit in the prompt, I get a whole ton of errors there too, I'll repost them and the out of range error in a minute.

---

### Post by stabf on 2009-03-29
the error i get is "attempt to access beyond end of device sda rw=0" and then a bunch of numbers

---

### Post by abn91c on 2009-03-29
other than the mouse and KB you have any other external peripherals attached? if so remove them

---

### Post by stabf on 2009-03-29
I don't have any peripherals,

I was wondering, how would i go about installing Ubuntu to say, a flash drive? Its the only external drive i have.

---

### Post by presence1960 on 2009-03-29
> **stabf said:**
> I have been attempting to fix this issue with fixes from this website for at least the last 2 hours. I'm seriously debating just saying "screw it" and labeling Ubuntu as a complete waste of time.

[https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks)

[http://www.howtoforge.com/install-ubuntu-with-software-raid-10](http://www.howtoforge.com/install-ubuntu-with-software-raid-10)

[http://ubuntuforums.org/showthread.php?t=1108773](http://ubuntuforums.org/showthread.php?t=1108773)

Hopefully these will help.

---

