---
title: "GRUB is having a bit of trouble... Weird trouble..."
date: 2009-06-06
forum: General Help
---

### Post by Xanmar on 2009-06-06
I will first give you the scenario of what led up to GRUB not being able to boot into Vista:
Firstly, I bought a 8GB Cruzer Micro USB drive to put my Wii backups on, but Wii ISOs are 4.3GB, so I can only hold one on it at a time. The tricky thing is that the USB drive needs to be formatted to WBFS to work on the Wii, which is fine, but then Windows won't see it at all. So I got Paragon Partition Manager 9.0 so that I could use the other 3.6 or so gigabytes for file transfering etc. So I split the partition with Paragon Partition Manager, and formatted it into FAT32. It then asked me to restart the computer, and now GRUB will no longer boot into Windows. It will hang at the "Starting up..." screen and underneath "Starting up..." will be a series of random characters that I've never seen before, and overlapping that will be the standard blinking command-line cursor.
I have absolutely no idea what's happening, and subsequently have absolutely no idea how to fix it. Any help would be greatly appreciated.

---

### Post by VMC on 2009-06-06
Can grub boot anything else?

Just in case, from either livecd or Ubuntu from a terminal (Applications > Accessories >Terminal), type the following:

sudo grub. then you will get this prompt: >grub 

```
find /boot/grub/stage1
```

exit grub

still from terminal type:

```
cat /boot/grub/menu.lst
```

---

### Post by Xanmar on 2009-06-06
Thanks, but what exactly was this supposed to do? Do you want me to post what it says?
If so:
```
grub> find /boot/grub/stage1
 (hd0,4)

```Then:

```
xanmar@xanmar-desktop:~$ cat /boot/grub/menu.lst


title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        1bb8c7ce-c3da-4f74-8c96-db0390667235
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=1bb8c7ce-c3da-4f74-8c96-db0390667235 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        1bb8c7ce-c3da-4f74-8c96-db0390667235
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=1bb8c7ce-c3da-4f74-8c96-db0390667235 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        1bb8c7ce-c3da-4f74-8c96-db0390667235
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=1bb8c7ce-c3da-4f74-8c96-db0390667235 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        1bb8c7ce-c3da-4f74-8c96-db0390667235
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=1bb8c7ce-c3da-4f74-8c96-db0390667235 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        1bb8c7ce-c3da-4f74-8c96-db0390667235
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```And yes, it can boot Ubuntu just fine.

---

### Post by Xanmar on 2009-06-07
UPDATE:

Here are pictures of exactly what I'm seeing. Anybody else having this problem?
[http://masterslackers.net/images/fukkengrub1.JPG](http://masterslackers.net/images/fukkengrub1.JPG)
That's my startup screen, with Grub. It's always been like that, so anything seen on that page isn't the problem.



[http://masterslackers.net/images/fukkengrub2.JPG](http://masterslackers.net/images/fukkengrub2.JPG)
After this, it just hangs forever. Never does anything. Anybody? Answers?

---

### Post by dandnsmith on 2009-06-07
The format of the 2nd img is, I think, significant.
Looks like what happens if the 1st stage grub bootloader gets corrupted - what it shows is 4 'random' characters in place of the usual GRUB> prompt.

As to what really happened, I cannot imagine, but the corruption is probably in the Partition Boot Record in /dev/sda1, and is getting invoked by the entry for Vista in the grub.conf/menu.1st.

Any chance you have a backup copy of the first block of sda1 which you can try restoring from?

Later: I'm not so sure about the 1st block - perhaps it is the 2nd that is corrupted.
Possibly the thing to try, if it is appropriate for Vista, is *fixboot* (but not *fixmbr*).

---

### Post by Xanmar on 2009-06-07
No, sorry I don't. Is there any way I can recover it manually?

---

### Post by dandnsmith on 2009-06-07
Sorry, bit of x-posting due to us both hitting it together.

I'll still suggest *fixboot*.

I don't really know whether there is an internal to the filesystem copy of the vital bits (similar to the 'spare' copy in FAT).

I've found that xxd (or was it xdd?) useful for looking at what is in those initial blocks.

---

### Post by Xanmar on 2009-06-07
EDIT EDIT: OKAY, Nevermind about that either...

I found that GRUB exists on (hd0,4). I was able to run setup on it again, but nothing changed...

Here is my device info from "sudo fdisk -l"
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
102 heads, 51 sectors/track, 120173 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      114268   297209852    7  HPFS/NTFS
/dev/sda2          114269      120173    15358905    5  Extended
/dev/sda5          114269      119907    14667013+  83  Linux
/dev/sda6          119908      120173      691840+  82  Linux swap / Solaris

```

---

### Post by Xanmar on 2009-06-07
New update:

I tried installing GAG, or the "Graphical Boot Manager", in hopes of it completely overwriting GRUB, but that's not the case. The only thing that's changed is when I select Windows to boot up, the random characters are no longer there, and they are replaced by this:
[http://www.masterslackers.net/images/fukkengrub3.jpg](http://www.masterslackers.net/images/fukkengrub3.jpg)

Are you guys as worn out as I am? -___-

Does anybody know of an MBR program that will overwrite GRUB, but still allow me to boot both Linux, and Windows?

Also, I don't think that I CAN do fixboot, or fixmbr(whatever it is), because I've lost my original recovery CD. But I burned another one, and I think it actually has to start loading into Windows before the CD will start to take effect, so it's completely useless. I just need a program that can overwrite GRUB.

---

### Post by dandnsmith on 2009-06-07
That last thing has convinced me that there isn't anything wrong with GRUB/GAG - the installation was correct in both cases.
The error shows when you try to hand control to the Windows boot sequence.

Back in the XP days, I discovered [multibooters](http://www.multibooters.co.uk/) site, which is devoted to the Windows boot processes.
If you're up to a bit of reading, there may be a solution there.
As I don't have Vista (and would prefer not to tangle with it), I haven't kept up-to-date, but it seemed to have originated with a guy I came to respect for his depth of knowledge about the problems with the boot processes.

---

