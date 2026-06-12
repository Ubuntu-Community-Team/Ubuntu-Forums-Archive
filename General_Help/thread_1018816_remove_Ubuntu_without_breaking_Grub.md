---
title: "remove Ubuntu without breaking Grub"
date: 2008-12-22
forum: General Help
---

### Post by EvilRobotDrew on 2008-12-22
I have a laptop, with an 80Gb HD partitioned as follows:

sda1 - 10Gb  - Ubuntu - BOOT PARTITION, Grub reads /boot/grub from here
sda3 - 49Gb  - /home (in both Ubuntu and Fedora)
sda4 - 13Gb  - Fedora
sda2 - 2.5Gb - Swap

I like Ubuntu, but the time has come to remove it and use Fedora exclusively (fedora works better with my hardware, i cut my tux teeth on Ubuntu, and i want something different). 

If, while in Fedora i deleted everything in the Ubuntu Partition except /boot, and booted into a live CD, made the /home partition bigger (leaving 200mb for /boot); would I break grub?

---

### Post by unutbu on 2008-12-22
What you describe should work. You'll be able to boot Fedora, though not Ubuntu, of course.

In case I'm wrong, or if you want to consider another option, all you would have to do is boot from a LiveCD, type
```

sudo grub
grub> root (hd0,3)
grub> setup (hd0)
grub> quit
```

Doing so will install a GRUB bootloader on the MBR which points to (hd0,3) aka /dev/sda4.
Then the /boot/grub/menu.lst in sda4 will be read and control the rest of the boot process.

---

### Post by EvilRobotDrew on 2008-12-23
deleting everything except /boot and shrinking the partition worked. I like the idea of a separate /boot partition, and this makes things much easier later if i decide to reinstall Ubuntu or install another distro alongside Fedora.

thank you for the idea tho, your idea would have worked with just a bit of tweeking (I would have had to recreate menu.lst in fedora's /boot/grub).

now that i have a separate /boot and /home partitions and fedora installed it is time to find another project to work on while ignoring my family over the holidays.

---

### Post by Herman on 2008-12-23
> I like the idea of a separate /boot partition, and this makes things much easier later if i decide to reinstall Ubuntu or install another distro alongside Fedora. :) It would be called a 'Dedicated GRUB Partition', now, since it doesn't belong to an operating system anymore.
I agree with you 'Dedicated GRUB Partitions' are really cool! :)

The first web site I know of to use the term 'Dedicated GRUB Partition' was [Grub Grotto]("http://www.troubleshooters.com/linux/grub/index.htm") by Steve Litt,If you look into that link, you'll learn that it isn't the quite the same thing as a 'Separate /boot Partition'.

A 'Separate /boot Partition' is a partition that is part of an operating system, and it's registered in the /etc/fstab file of an OS as /boot, so that the operating system that owns it will install it's kernels there. 
A 'Separate /boot Partition' can just as easily contain LiLo instead of GRUB, although it is quite possible to have both. 
The main purposes for having a 'Separate /boot Partition' are, 

[LIST]
[*]in the old days it made it possible to restrict the physicl location of the kernel within the first 8 GB of the hard drive where the BIOS could address it to avoid GRUB Error 18, and thus make use of a larger hard disk than the computer's BIOS was designed to handle.
[*]In modern times for an installation with an encrypted / file system or a RAID array.
[/LIST]
The disadvantage of a 'Separate /boot Partition' is it's tricky to get more than one operating system to share the same /boot, because they will overwrite each other's menu.lst files, so you (normally) need a different /boot partition per operating system.

A 'Dedicated GRUB Partition', on the other hand, is entirely 'operating system independant', and makes it easier for you to boot as many operating systems as you like. :)
Each operating system can then keep it's kernels in it's own /boot directory or 'Separate /boot Partition' and be free to update it's own menu.lst with update-grub when there's a kernel update.
That's a good way to set up a multiple boot computer.

I hope you don't mind me interupting here, maybe I'm bothering you with stuff you don't really need to know, or care about. I just had to get my 2 cents worth in here though. The main thing is to keep on having fun with GRUB.

Regards, Herman :)

---

### Post by EvilRobotDrew on 2009-01-19
thank you Herman, you post was definately informative. I guess i should check my topics more often :P

---

