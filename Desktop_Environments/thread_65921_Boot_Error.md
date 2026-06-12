---
title: "Boot Error"
date: 2005-09-15
forum: Desktop Environments
---

### Post by IdolizingStewie on 2005-09-15
I dual boot my system with WinXP. I'd had it on XP for a few days and wanted to boot into Ubuntu today. When I got into GRUB and selected Ubuntu, it got through the first few lines of the process, but came up with a disk write error like this: (there might be some spelling errors since I'm doing this from a rather blurry picture I took of the screen)

```
...
initrd /boot/initrd.img-2.6.10-5-386
    [linux-initrd @ 0x11b24000, 0x433000 bytes]
savedefault

Error 29: disk write error

Press any key to continue...
```

Pressing a key sends me back to the GRUB menu, where I tried to boot into recovery mode with the same results. It's been a couple of days, but I haven't the foggiest idea what I could have done to cause this if it was indeed my fault. Is there a solution here other than copying anything important to my Windows partition or the FAT32 partition i store most stuff on anyways and reinstalling? It seems like I remember seeing a recovery command from the install CD similar to the Windows one, but I don't really know what I'm doing - if I just made it up or what the command is or how it works.

---

### Post by mlomker on 2005-09-15
You could try booting to a liveCD such as Knoppix and see if the partition is readable.  It's possible that the partition is corrupt and you just need to run fsck (checkdisk) on it.

---

### Post by IdolizingStewie on 2005-09-17
So I finally managed to get my hands on a knoppix disk and happened to try rebooting into ubuntu one more time, and it worked perfectly this time. I don't have a clue why it didn't think it could write to the RAM, I'm just happy it's working now. I was getting really tired of windows.

---

### Post by Flegg on 2005-09-18
does anyone have any ideas what would cause this the other way around? (can boot into ubuntu, but get disk write error when trying to get into XP?)

Thanks

Flegg

---

### Post by mlomker on 2005-09-18
[QUOTE=Flegg]does anyone have any ideas what would cause this the other way around? (can boot into ubuntu, but get disk write error when trying to get into XP?)
[/QUOTE]

Try booting up on your WinXP cd and have it run checkdisk on the partition.

---

