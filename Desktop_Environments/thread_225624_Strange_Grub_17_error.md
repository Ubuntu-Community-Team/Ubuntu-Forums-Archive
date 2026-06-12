---
title: "Strange Grub 17 error"
date: 2006-07-30
forum: Desktop Environments
---

### Post by uber on 2006-07-30
So I'm pretty new to this whole Linux thing (as everybody here is, I would guess), and I'm experiencing an odd problem that I would like to know how to fix.

I downloaded the x86 Live CD from the Ubuntu web page, mounted it and installed Dapper on a new WD Cavair SATA 160 GB HD. Everything went smoothly and perfectly throughout the install process. I reboot, remove the CD and when starting I get an error message that says something like this:

Error Grub 17.

The really odd thing is that when I choose to instead boot from the Live CD, and select "Boot from first Hard Disk," I get a menu asking me which operating system I would like to boot (I have XP SP2 installed on a different IDE drive) and from there everything works perfectly.

As well, if I don't have the SATA drive configured as a JBOD in the BIOS settings I get a Grub 21 error instead of a 17.

So my question to all the masters out there is, what is going on, and, how do I fix it?

Of further interest, my BIOS boot setting refuses to recognize my SATA drive as a boot option unless it is configured as a JBOD. Any ideas as to why this would be happening?

---

### Post by rowanparker on 2006-07-30
Could you use the LiveCD to boot it then reinstall grub?

---

### Post by uber on 2006-07-30
I can use the LiveCD to boot normally, which is the really strange part. If I select "boot from first disk" in the LiveCD menu, and then select my Ubuntu disk, everything works fine and dandy. But why should that work and not Grub?

---

### Post by rowanparker on 2006-07-30
Use the LiveCD and choose "Boot From First Disk". When you've booted into Ubuntu open up a terminal and run:```
sudo grub-install hd0 #Or whereever you want it
```

Then reboot, without the disk in, Does it still happen?

---

### Post by uber on 2006-07-30
I ran the command, and here is the output I got:
```
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hdc
(hd1)   /dev/hdd
(hd2)   /dev/sda

```

hd2 is my Ubuntu drive. I haven't tried rebooting yet, as I am in the middle of something else, but I'll post the status on that shortly.

---

### Post by rowanparker on 2006-07-30
OK, that says it worked.
So only a reboot can see.

---

### Post by uber on 2006-07-30
Ok, so I rebooted, and got farther than I normally do. This time, I was presented with a menu, asking me to select which OS to boot. There were several Ubunutu kernels listed, along with Windows XP. But, after I choose an OS, I go this message:
```
      Booting 'Ubuntu Kernel 2.6.15-26-386'
root (hd2,0)
      Filesystem type unknown partition type 0x7
Kernel /boot/vmlinuz-2.6.15-26-386 root=dev/sda1 ro quiet splash

Error 17: Cannot Mount selected partition
```
When I boot from the LiveCD, select 'Boot from first hard disk' I am presented with the exact same OS menu, but selecting my Ubunutu kernel allows me to boot into Linux.

What is going on!?!?!

---

### Post by rowanparker on 2006-07-30
That must be a grub problem as you can boot fine from the CD. Try fiddling with the /boot/grub/menu.lst on your /dev/sda1.

---

### Post by uber on 2006-07-31
I believe I already tried fiddling with the menu.list file, and nothing came of that. 

Is there an alternative to GRUB that I can try?

---

### Post by Ramses de Norre on 2006-07-31
Can you post the exact configuration of drives, partitions and os's and your menu.lst?

---

### Post by uber on 2006-07-31
I'll do that as soon as I get home. Is there a simple command I can run, or do I need to open all the files and paste the contents?

---

### Post by uber on 2006-07-31
Here is the output of 'sudo fdisk -l' I found it another one of my threads. Does this give you the kind of information you need?

```
Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdc1 * 1 9728 78140128+ 7 HPFS/NTFS

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdd1 * 1 24321 195358401 7 HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 19079 153252036 83 Linux
/dev/sda2 19080 19457 3036285 5 Extended
/dev/sda5 19080 19457 3036253+ 82 Linux swap / Solaris
```

---

