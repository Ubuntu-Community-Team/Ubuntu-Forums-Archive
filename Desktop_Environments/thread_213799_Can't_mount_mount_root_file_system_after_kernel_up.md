---
title: "Can't mount mount root file system after kernel update"
date: 2006-07-11
forum: Desktop Environments
---

### Post by JohanSwe on 2006-07-11
I can't mount root file system after updating Ubuntu today. My fstab got a new entry and all my previous settings in fstab (except press escape for list) is lost.

Using the first alternative in my bootlist stops with a blinking line after the text: booting kernel (I think).

It's the same for all console booting alternativs (also for old kernels).


For the second graphical alternative the standard Ubuntu splash screen is shown but the computer stops (freezes) after this:
> Loading essential drivers... ok
Mounting root file system...
Waiting for root file system.... 

I have been compiling the last kernel before the update when following [this guide]("http://ubuntuforums.org/showthread.php?t=197471&highlight=3d+radeon") for installing ATI's driver for 9200SE. The driver work just fine.

Also I have been following [this guide]("http://ubuntuforums.org/showthread.php?t=41709&highlight=Howto%3A+splashy") to install splashy. All (not many) fstab.list modifications for splashy is gone.

To try to fix the booting problem edited back to the Ubuntu standard "ati" in xorg.conf. But it shouldn't matter since both drives were working and I even can't boot into a consol.

The Ati driver and Splashy was installed many boots ago and have worked just fine.


This is strange. Anyone who can help me :confused:

---

### Post by JohanSwe on 2006-07-12
I still need your help. 

But I have been doing some progress. I think the problem was and is mounting partitions.

This is the partitions grub sees: hd5, hd6
And the partitions in /dev/: sda1, sda6, sda7

The paths in my fstab.lst is with hda. That's strange since I got i s-ata disk. I changed the kernel path from hda6 to sda6 and now I'm able to but to a consol. Xorgs is not working and I think it is because I'm told while booting that /dev/sda7 isn't mounted, and that's where my homefolder is probably with some necessary configuration files?

[INDENT]*Unedited - doesn't work*
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/**hda6** ro quiet quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot
[I]
Edited - does work[/I]
title		Ubuntu, kernel 2.6.15-26-386 sda6
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/**sda6** ro quiet quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot[/INDENT]

It is strange that the booting process can't mount sda7 since I can mount it from my live cd.

[LIST]
[*]How come the paths in fstab is to **hd**x while I got a s-ata disk and the partitions in /dev is **sd**x?

[*]And why does grub think it is **hd**x partitions?

[*]Why can't the booting process mount sda6 = root but not sda7 = home folder?

[*]How could the kernel upgrade effect this?
[/LIST]

Please help me ](*,)

---

### Post by JohanSwe on 2006-07-12
- Problem solved - 
I changed graphics driver to vesa

---

