---
title: "help, i ran swapon on my / partition!"
date: 2006-06-15
forum: Desktop Environments
---

### Post by sam hassell on 2006-06-15
hi,

I just stuffed up and turned my primary partition into a swap drive. Not surprisingly, grub gets confused when trying to boot. :-({|= 

i've booted using a breezy live cd (im running dapper) and have tried a few little things, but nothing has worked.

Help please?

---

### Post by frup on 2006-06-15
correct me if i am wrong... but doesnt that mean you formatted it?

---

### Post by Amon_Re on 2006-06-15
Make sure the filesystem is recognised as an ext2 or whatever drive & not as swap, boot with a live cd, and run "sudo fdisk -l" to check.

You might be able to repair/recover data with TestDisk ([http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"))

---

### Post by sam hassell on 2006-06-15
frup: pls dont tell me that :) it happened really quickly, so maybe it delinked without removing the filesystem.. *fingers crossed*..

amon: it shows this:

/dev/hdc1   1  2031   16313976   83   Linux
/dev/hdc2  2032  2096   522112+   82   Linux swap / Solaris

so it looks like the main partition is still in tact..

I'll look into TestDisk now.

---

### Post by cotcot on 2006-06-15
I suggest to try to reinstall grub. For instance by chroot from the install CD into your /dev/hdc1 and grub-install /dev/hdc or any other method. You can find some by searching in this forum on 'MBR messed up4.

---

### Post by Ramses de Norre on 2006-06-15
Test disk shouldn't be necesary then, mount the partition from the live disc and check for changes in /etc/fstab (correct filesystem type and mountpoint) and /proc/swaps (remove any instances saying the / partition is swap).

---

### Post by sam hassell on 2006-06-15
ramses & cotcot, it won't let me mount it. error message is

"/dev/hdc1 looks like swapspace - not mounted"

trying with "-t ext3" (which the drive should be) gives wrong fs type.

---

### Post by sam hassell on 2006-06-15
Things dont look good according to [http://answers.google.com/answers/threadview?id=102981]("http://answers.google.com/answers/threadview?id=102981"). 

I guess now is a good time to d/l & burn a shiny new Dapper CD and reinstall.

Lucky I moved /home to its own partition the other day and backed up my fstab and xorg.conf...

Thanks for all your help guys!

---

