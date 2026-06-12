---
title: "Triple-booting Vista x64 - Ubuntu x86 - XP x86"
date: 2009-03-07
forum: General Help
---

### Post by gh0sst on 2009-03-07
Hello!

I have installed Ubuntu x86 while having Vista x64 installed... and the booting choice screen works just fine... I've edited from /boot/grub/menu.lst to boot Vista by default... it works great.

But here's my problem:

If I install Windows XP x86 now... will the new operating system appear in the booting choice screen, and can menu.lst be edited so that WinXP can be set the default OS ?

Thanks in advance!

---

### Post by howefield on 2009-03-07
Windows XP will overwrite grub with its own bootloader, you will need to reinstall grub once you have xp installed.

---

### Post by gh0sst on 2009-03-07
After installing XP, in order to reinstall the grub, will I have to use the ubuntu install CD to boot into Ubuntu and then use [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") guide to reinstall grub ?

---

### Post by hexanol on 2009-03-07
You could indeed boot from a live CD to reinstall grub. If you have a floppy drive or a USB stick laying around, you could also [install grub on it]("http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy") and then, after installing xp, you would only need to boot from your floppy/usb stick and enter commands similar to these (in the grub prompt)

```
grub> root (hdX,Y)
grub> setup (hdX)
```

And if you installed XP correctly (i.e. didn't mess with the other partition), you would see back your original grub menu, and after that you would only need to edit the menu.lst file to add a entry for XP.

And yes, the guide seems correct.

---

### Post by gh0sst on 2009-03-20
I have installed Windows XP today alongside Vista and Ubuntu.

I have reinstalled grub right after I installed XP, but now I have another problem: I can only boot into XP from grub and I can't get into Vista.

All 3 OSs are installed on one harddisk. What should I do so I can boot any OS I want (ubuntu / Vist / XP) ?

---

