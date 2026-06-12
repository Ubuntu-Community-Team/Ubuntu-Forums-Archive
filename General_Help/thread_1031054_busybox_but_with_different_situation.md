---
title: "busybox but with different situation"
date: 2009-01-05
forum: General Help
---

### Post by DangerIsGo on 2009-01-05
Here's the whole story so you guys can get a better understanding of the pain i went through this weekend.  I initially had XP installed on my comp.  Then I wanted to also install ibex and windows 7.  After deciding to scrap the idea of installing windows 7, I just went with a dualboot of XP and ibex.  So shrinking my 140gb partition to 100GB for xp and 40 for ibex, I continued to install ibex.  After letting it do its upgrades, I figured I may try to install my raid card (RocketRaid 2300...I was having a lot of issues w/ driver building in the past and gave up altogether on using linux since I need my raid0 arrays (2x750GB each for 2x1.5TB arrays).  So after doing some digging, and messing with the driver's source code, I was able to get them successfully installed and working.  So at this point, I had XP accessible and ubuntu accessible with my raid arrays accessible on both OSs.  Now comes the stupid part.

I wanted to load XP SP0 to test a game that I have been wanting to play for a long time (long story short, it doesn't work on XP or 2000, but I wanted to do some testing).  So I decided to install xp sp0 on the xp partition, letting it overwrite the original XP and MBR and then I would just re-install grub at a later time.  Well, somehow, XPs partition edition during setup screwed up (and it most definitely was not human error as I double checked the partition that was to be formatted and it was indeed the 100GB) and the whole disk got scrapped.  No biggie.  I did it before, I could do it again, right? wrong.  

After playing with XP and reloading XP sp3, I then proceeded to install ubuntu back again.  Everything dual booted initially fine.  My main hdd was sde (this is installing with my raid card plugged in) and xp's partition was 1 while ubuntus was 5.  Now comes the frustrating part.  I installed my drives like I did previously, but upon restart, I got the busy box.  After waiting several minutes, I finally was able to get in but w/ no RAID card .  To shorten up this post, the following is a list of things I have done and their results, in the end unable to replicate what I initially did for a working dual boot system.

- Installed ubuntu with no other drives connected - after connecting the drives, neither OS was seen.  I had to manually edit the menu.lst file to allow XP to be booted, but ibex still refused to boot normally.

- Using a Live CD, I was able to get in and re-do the grub setup...to no avail.  The result of find /boot/grub/stage1 was (hd4,5) and after doing root (hd4,5) and setup(hd4), it didn't fix it.  Even trying to do (hd0,5) produced an unable to find error.

- Playing with the menu.lst file to enable and disable the maps at the very bottom (between hd0 and hd4) along with adding rootdelay=130 at the end of the kernel string.  That didn't work either. Busybox still came up.

- I tried waiting the busy box out and although I could get in, the RAID card did not function which leads me to believe something screwed up during boot.

- I have tried re-arranging the mapping done in device.map (between hd0 and hd4) but that didn't work either.  still gave the busybox.

Anything else that I could try would be a big help.

The output of fdisk -l shows a format like this:
/dev/sda - 750GB HDD - RAID0 array 1
/dev/sdb - 750GB HDD - RAID0 array 1
/dev/sdc - 750GB HDD - RAID0 array 2
/dev/sdd = 750GB HDD - RAID0 array 2
/dev/sde - 150GB HDD - main drive partitioned to 100/40/2 (2 for swap)
/dev/sdf - 500GB HDD - spare HDD

I'm not on my comp right now, so I can show the real output, but I know it looks something like that.

I have tried installing many times while changing the grub install location (advanced in step 7) to (hd0), (hd4), /dev/sde, and /dev/sda (when it was that one), and neither of them worked after installing the raid card(except initially).  

My guess into this, is that raid array drives are superseding the main drive in the list, which is why they are getting 0-3 and the main drive is hd4.   Along with that, the first installation was probably some kind of magical fluke that was able to work, but since then, i have had no such luck on reproducing it.  Any help would be greatly appreciated.  Thanks.

---

### Post by fjgaude on 2009-01-05
Have you tried having your BIOS point to the /dev/sde drive, the partition from where the boot is to occur?

---

