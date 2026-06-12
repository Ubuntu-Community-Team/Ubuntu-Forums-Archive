---
title: "Ubuntu won't boot"
date: 2005-12-31
forum: General Help
---

### Post by Hitchhiker427 on 2005-12-31
Hello, I'm new to Ubuntu.  I played around with in on a live CD a while ago, and I used to have it installed on my old computer, but after upgrading my PC, I'm running into some annoying errors.  I've searched these forums many times and read alot of threads, but am unable to fix my problem.

Also, to note, I dual boot Ubuntu/XP (separate harddrives) with XP as my primary... for now.

Ok, first things first, my hardware:

AMD X2 3800+                          <-- pretty sure that's the culprit
NVidia GeForce 6600
1024 MB RAM single-channel
ASRock 939Dual-SATA2 MB

   So, first, I tried to install Ubuntu.  This worked fine.  My network card wouldn't work, but I just plugged in a replacement that was lying around here.  Grub managed to recognize my XP installation and everything.  Unfortunately, when I restarted my computer, I was unable to boot into Ubuntu.  It gave me an error message that I will show below.
   I browsed the forums and discovered that the linux kernel included with my Ubuntu installation was not compatible with the dual-core processor, so I figured that might be the problem.  I heard that the kernel needs to support smp and k7 is recommended for my CPU. Alright, after browsing some more, I found out how to upgrade my kernel.  I used this command below:
```
sudo apt-get install linux-k7-smp
```
   All seemed to work out fine.  It installed, and I was able to restart my computer.  So, I proceeded to install my apps via automatrix, and install the updates to Ubuntu.  After getting it set up, I tried to restart again, and it worked flawlessly.  
   Later, I needed to get onto my Windows installation to do something.  After I was done, I tried to reboot into Ubuntu and got another error message.  After failing to figure out the problem I reinstalled Ubuntu and tinkered some more.  The problem seems to be that I can't boot Ubuntu after booting to Windows.

These are the error messages I received:

[Trying to boot Ubuntu (new version) normally]:
```
	Booting 'Ubuntu'

root (hd0,0)
  Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.12-10-k7-smp root=/dev/hdc1 ro quiet splash
   [Linux-bzImage, setup=0x1434b0]
initrd /boot/initrd.img-2.6.12-10-k7-smp
   [Linux-initrd @ 0x1fa7c000, 0x573baa bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
Loading, please wait...
mount: Mounting /dev/hdc1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/ .static/dev failed: No such file or directory
mount: Mounting /dev on root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init
```

[Trying to boot Ubuntu (new version) in recovery mode]:
```
Begin: Running /scripts/local-top ...
Done.
Begin: Running /scripts/local-premount ...
[4294679.908000] Attempting manual resume
[4294679.908000] swsusp: Suspend partition has wrong signature?
Done.
[4294679.916000] EXT3-fs error (device hdc1): ext3_check_descriptors: Inode bitm
ap for group 384 not in group (block 2147483647)!
[4294679.916000] EXT3-fs: group descriptors corrupted !
mount: Mounting /dev/hdc1 on /root failed: Invalid argument
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
mount: Mounting /root/dev on /dev/ .static/dev failed: No such file or directory
mount: Mounting /dev on root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init


BusyBox v1.00-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#

```

If I try to boot to the old kernel, I get an error message similar to the one above.  Also, when I first installed Ubuntu and DID NOT upgrade the kernel, I also got an error message similar to the one above.

Here is my /boot/grub/menu.lst:
```
title		Windows XP
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title		-------
root

title		Ubuntu 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7-smp root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-k7-smp
savedefault
boot

title		Ubuntu (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7-smp root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.12-10-k7-smp
boot

title		Ubuntu <old> 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdc1 ro #quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu <old> (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		-------
root

title		memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

```

/boot/grub/device.map:
```
(hd0)	/dev/hdc
(hd1)	/dev/hdd

```


Please remember that I am really new with this, and detailed instructions would be great.  If this is not enough info, I can post the contents of any of the files if you think it would help.  I'd really like to use Ubuntu, but problems like these are really off-putting.

---

