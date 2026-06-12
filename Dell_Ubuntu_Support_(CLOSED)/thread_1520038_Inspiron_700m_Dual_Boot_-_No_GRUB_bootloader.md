---
title: "Inspiron 700m Dual Boot - No GRUB bootloader"
date: 2010-06-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by muliganstew on 2010-06-29
I'm not quite sure how to pose my question so I'll just go over what has happened to my laptop over the last few days.

So I have a 700m where I have Ubuntu 10.04 and Windows XP dual booted.  I decide that I want to try Windows 7 so I install Windows 7 over the XP partition.  However, I've read that installing a windows os will over ride the GRUB boot loader, and I need to reinstall it.  The most common way I've seen is that I should use the Live-CD and reinstall the boot loader from there.

However, the 10.04 Live-CD does not boot with my 700m.  After I see the ubuntu logo, I'm given a black screen.  After reading around, I suspect that the problem is that the 10.04 Live-CD has an issue with the graphics chipset in the 700m:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

However, the workarounds I found (also found on the link above) require that I be able to boot into ubuntu in the first place which I can't because windows 7 has made the GRUB boot loader unavailable to me!

So far, I've been trying to manually install the GRUB boot loader from windows, but I've been having difficulties.  I'm going to try a few more things (perhaps using a different version of the live cd?), but if anyone can lend some advice that would be great.

Thanks, this has been a very frustrating experience.

---

### Post by wilee-nilee on 2010-06-29
> **muliganstew said:**
> I'm not quite sure how to pose my question so I'll just go over what has happened to my laptop over the last few days.

So I have a 700m where I have Ubuntu 10.04 and Windows XP dual booted.  I decide that I want to try Windows 7 so I install Windows 7 over the XP partition.  However, I've read that installing a windows os will over ride the GRUB boot loader, and I need to reinstall it.  The most common way I've seen is that I should use the Live-CD and reinstall the boot loader from there.

However, the 10.04 Live-CD does not boot with my 700m.  After I see the ubuntu logo, I'm given a black screen.  After reading around, I suspect that the problem is that the 10.04 Live-CD has an issue with the graphics chipset in the 700m:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

However, the workarounds I found (also found on the link above) require that I be able to boot into ubuntu in the first place which I can't because windows 7 has made the GRUB boot loader unavailable to me!

So far, I've been trying to manually install the GRUB boot loader from windows, but I've been having difficulties.  I'm going to try a few more things (perhaps using a different version of the live cd?), but if anyone can lend some advice that would be great.

Thanks, this has been a very frustrating experience.

If you boot the cd and hit the f6 key and choose nomodeset to start with hit esc and try and boot it may work. Not knowing what you have done so far from windows since you can't get into Ubuntu unless it is a ***wubi*** install I'm hesitant to go any further here other then if it is a dual boot and you get in with a live cd follow this link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

A karmic cd would work as well and any cd that has grub2.

From your link.
> From the LiveCD:

1) At the purple screen with a keyboard and stickfigure, press Enter to get to the menu.

2) Hit Enter to select your language, and then press F6 and then Esc.

3) Add "i915.modeset=1" after "quiet splash".

4) Press Enter to boot the LiveCD. 

---

### Post by muliganstew on 2010-06-29
Okay so using a karmic cd I was able to boot the Live -CD (I'm actually writing this from the Live-CD).  So I followed the instructions on the link you provided, and I'm going to try and rebooting and see if it works after this post.  However, I do have one question:

So fdisk -l gives me:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        2578    20659590    7  HPFS/NTFS
/dev/sda3            2579        4864    18362295    5  Extended
/dev/sda5            2579        4763    17550981   83  Linux
/dev/sda6            4764        4864      811251   82  Linux swap / Solaris

sda1 is the utility; sda2 is probably my windows, and sda5/sda6 is for my ubuntu install.  What is the sda3?  When I run sudo blkid I get:

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0B0A" TYPE="vfat" 
/dev/sda2: UUID="7C2C7BE92C7B9CB8" TYPE="ntfs" 
/dev/sda5: UUID="aeba9617-21cc-456f-b7f5-5aaa34f650f6" TYPE="ext4" 
/dev/sda6: UUID="132773ef-4887-4b0a-9433-9d36fc0901a3" TYPE="swap" 

And the sda3 is not even listed.  I was just wondering what that means.  Anyway I'm going to try and reboot and see if anything has changed.

---

### Post by muliganstew on 2010-06-29
Okay, so I reboot my laptop and Windows no longer boots first (which is good), however, GRUB 1.5 loads (I'm presented with a terminal like interface).  I'm not quite familiar with this interface for GRUB so I'm not sure what course of action to take.

For now I'm going to try and play around with this interface and try some of the other solutions I found on the link you provided.

(sorry for the double post)

---

### Post by wilee-nilee on 2010-06-29
So hows it going were you able to boot into Ubuntu and run in the terminal. ```
sudo update-grub
``` 
To load W7 into the grub bootloader.

sda3 is a extended partition that encases your Lucid install, when you do a auto install it is automatically used. This allows you to put more primary partitions inside it the a standard HD which only allows a total of 4.

So in the future if you were manually building your Linux install and wanted more the 4 primary partitions you would put a extended in first then the subsequent primaries inside.

---

### Post by wilee-nilee on 2010-06-29
The best thing to do now is don't mess around, boot the live cd and download ans run the bootscript in my signature, post it in code tags with the description or just highlight the txt and click on the # in the panel.

I suspect if you followed the grub2 install with the cd that you just loaded the wrong partition.

It's not grub 1.5 it is grub2 official the number is grub 1.98, we call it grub2, I only mention this we are on the same page.

---

### Post by wilee-nilee on 2010-06-29
So from the live cd you should run
```
sudo mount /dev/sda5 /mnt
``` Then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Then reboot and in Ubuntu 
```
sudo update-grub
```

If your still getting a command line then run the bootscript, and describe the command line is it just the word grub, or is a a login cli.

---

### Post by muliganstew on 2010-06-30
wilee-nilee thanks for all your help.  I'm not sure exactly really happened, but I ended up doing was following the instructions on the link you provided but used the Method 2 way.

And now everything is back to normal.  Yay!

---

### Post by wilee-nilee on 2010-06-30
> **muliganstew said:**
> wilee-nilee thanks for all your help.  I'm not sure exactly really happened, but I ended up doing was following the instructions on the link you provided but used the Method 2 way.

And now everything is back to normal.  Yay!

Hey whatever works, glad it's going.

---

