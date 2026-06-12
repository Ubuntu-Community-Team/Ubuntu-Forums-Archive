---
title: "LVM disk error?"
date: 2008-08-28
forum: Desktop Environments
---

### Post by johnnywellas on 2008-08-28
Hey there. Please excuse me for consuming some of your time, but I've been trying to solve this difficulty, without success.

So here's the deal: I was happily using my desktop, when suddenly it became kinda slow. I checked Azureus (Vuze?) and it was mentioning some disk write error messages on the active torrents. That is awkward, but "normal", given that that hard disk has already had some read/write trouble (had to put it in the freezer to recover data), this sometimes happens, and it is solvable with a restart, ext3 journaling does its thing wonderfully.

Basically, i restarted the machine, it loaded grub (as it is on another hard drive), then it showed the splash screen, and as soon as it tries to mount the lvm partition i have, which has the root filesystem from which grub boots, it freezes (black screen with just the cursor blinking on the top left corner of the screen).

Given the circumstances, i ran a thorough surface test of the hard drive, with a utility on Hiren's Boot CD (which, shamefully, has no kind of recovery functionality that can mount or manage LVM), just to make sure it wasn't some physical medium failure. The surface test showed no errors whatsoever, so, i suppose that the origin of this problem could be something like LVM "headers" (if this does make any sense), as if the information contained may all be there, but the volume is unmountable.

I'll explain how my machine has the hard drives set up:

HD1 - 80GB
- /boot
- Linux Swap
- 2 NTFS Partitions with a defunct WinXP installation which i'll completely redo as soon as i have time/patience

HD2 - 200 GB
- Windows Swap
- LVM with root mount point, where i have all the data
(^^ This is the partition that the system won't mount, and therefore boot)


The thing is, even partition managers won't recognize the LVM filesystem, it just gets classified as "Other". I really don't know of any applications that can be booted from a cd or whatever that can solve this.


I'll leave the contents of the menu.lst file, if it can be of any usefulness:


```
root (hd0,3)
kernel /vmlinuz-2.6-19-rt root=dev/mapper/WD2000VG-WD2000LV ro splash vga=795
initrd /initrd.img-2.6.24-19-rt
quiet
```

(i had to write it all by hand from the edit option on grub, i suppose i didn't commit any typos here - anyway it always worked fine like this, so...)


Summing it all up - i don't even need to fully restore the system as it were. Being able to handle the LVM volume would be enough, so that i can copy some stuff i still hadn't backed up to an external hard drive. Having to completely reinstall the system would be fair enough, but of course that keeping what i had would be the preferable solution.

Well thanks in advance for having read this far, hope i'm not being too bothersome or inconvenient.

Hope you guys can help me out on this. And thanks again.


---------------------

Oh, i almost forgot! I also tried to recover the system with the ubuntu installation cd, and when i get to the menu where i'm supposed to select the partition where to try to recover the system, i select the lvm volume, and i get an error message saying that an error occured while trying to mount that volume. Hope this can be of any further help or clarification. Thanks.

---

### Post by johnnywellas on 2008-08-28
OK, so i selected the command line option on grub (pressed "c"), type the whole menu.lst jargon manually (see code above) without the splash and quiet thingies (to be able to see the output), and i got to a bash shell (i suppose) that had "(initramfs)" just before the command line. I kinda explored the folders and stuff, and then i executed "./init" . It gave me a lot of output, amongst it the following errors:

> [    972.593860] EXT3-fs error (device dm-0): ext3_check_descriptors: Block botmap for group 256 not in group (block0)!
[    972.593860] EXT3-fs: group descriptors corrupted!

and therefore:

> mount: Mounting /dev/mapper/WD2000VG-WD2000LV on /root failed: Invalid argument

(again, i had to type all of this manually, still i suppose it's all ok, but there may be a typo here or there)

This kind of error Window$ would be solvable with chkdsk, on linux i suppose that fsck would do the trick, but it's not available at the command line.

I will try to find more information, as well as explore the "(initramfs)" filesystem in order to try and find some filesystem checking utility.

-----------------------------------------------------------------

I downloaded the standard desktop Ubuntu file, so as to be able to run the Live CD and try to fix this. 
fsck doesn't work with lvm, at least it STILL doesn't (the "fsck: fsck.lvm2pv: not found" probably suggests that a future implemantation will be due on future releases).

The lvm package wasn't present on the boot cd, so i downloaded the .deb file from the repository and after installing it, I fiddled around with lvm commands on the terminal. After entering "pvcreate /dev/sdb2", the scan commands showed the logical volume, volume group and physical group as apparently ok, still, and i can't remember exactly, some tab on those status reports said "unavailable". Also, some error message showed up saying that the device mapper version wasn't compatible. Very well. I rebooted, re-entered the live cd, reinstalled lvm package, and then, when i tried to do the pvcreate thing, i got some other error message, which said that the physical volume could'nt be created, to try and force the process (-ff or something).
I did so, and it seems that i busted the physical volume (probably created a new UUID or lvm meta tag or whatever). The device mapper on the live cd still won't allow me to do anything concrete (like creating the /dev/mapper group devices special files - vgmknodes)

Now the thing is - given that only the logical volume "encapsulation" would be broken (i haven't even been able to mount its filesystem, so, supposedly all the data is still there), is there any possibility of recovering the data, by retrieving the old identifier or something?

Thanks again! Hope that someone can help me on this, I've been tumbling on this for quite some hours with no success-

---

### Post by johnnywellas on 2008-08-30
I really don't like doing this, but... bump!

---

