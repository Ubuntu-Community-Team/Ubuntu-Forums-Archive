---
title: "Old kernels in boot menu-maverick 10.10"
date: 2010-10-24
forum: Desktop Environments
---

### Post by jamere on 2010-10-24
Hi all,
A few days ago I upgraded online from 10.04 to 10.10 without hitch, Nice job by developers, btw!

Anyway, GRUB insists on listing 4 old kernels in the boot menu, as well as, the newest two kernels. Had same problem in 10.04. Yes, I deleted them in Synaptic in 10.04. No trace of them in 10.10 Synaptic.

Would like to get rid of these 4 old kernel entries. Thanks much for any ideas on this.

---

### Post by claracc on 2010-10-26
I have found this thread [http://ubuntuforums.org/showthread.php?t=1152270](http://ubuntuforums.org/showthread.php?t=1152270), which indicates that after removing old linux-image -kernels from synaptic, you have to run in xterm sudo update-grub

---

### Post by jamere on 2010-10-26
claracc,

Thanks for the reply! However, I did do the "sudo update-grub" command in terminal mode.

These old kernel lines on the boot menu have been around for so long they feel like "family"! Can't get rid of them! :)

---

### Post by jamere on 2010-10-26
Just for grins, I decided to run "sudo update-grub" again with the following results:

```
jim@jim-laptop:~$ sudo update-grub
[sudo] password for jim: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Microsoft Windows XP Home Edition on /dev/sda2
Found Ubuntu 9.10 (9.10) on /dev/sda5
Found Ubuntu 9.10 (9.10) on /dev/sda6
Found Ubuntu 9.10 (9.10) on /dev/sda8
done
```

The update-grub did actually remove one of the four old kernels from the list, leaving three. Now I'm beginning to wonder if I really have removed "all traces" of the other three kernels from Synaptic.

claracc, you may have put me onto something! Thanks!

---

### Post by claracc on 2010-10-26
You are welcome.

Glad to help.

---

### Post by jamere on 2010-10-27
Well, I spoke too soon. Still have the problem. All four unwanted versions of the kernel are still showing on the boot menu. There are no traces of these unwanted kernels in Synaptic.

It looks like there would be a file where these unwanted kernel references could simply be edited out of the boot menu list.:confused:

Thanks anyway claracc!

---

### Post by halj32 on 2010-10-27
> **jamere said:**
> Well, I spoke too soon. Still have the problem. All four unwanted versions of the kernel are still showing on the boot menu. There are no traces of these unwanted kernels in Synaptic.

It looks like there would be a file where these unwanted kernel references could simply be edited out of the boot menu list.:confused:

Thanks anyway claracc!

if you have a look at your "update-grub" you will see that you have Ubuntu installed 3 times

Found Ubuntu 9.10 (9.10) on /dev/sda5
Found Ubuntu 9.10 (9.10) on /dev/sda6
Found Ubuntu 9.10 (9.10) on /dev/sda8
& XP on /dev/sda2

thats why you have 4 entries 1 for each install

---

### Post by jamere on 2010-10-27
Halj32, thanks for the insight! It's obvious now that the boot menu references are pointing at Ubuntu installs and the kernels within those installs. Too obvious for me! :)

I guess now the question is: How to go about removing old installs?

Any further insight? Thanks much, in advance!

---

### Post by halj32 on 2010-10-27
> **jamere said:**
> Halj32, thanks for the insight! It's obvious now that the boot menu references are pointing at Ubuntu installs and the kernels within those installs. Too obvious for me! :)

I guess now the question is: How to go about removing old installs?

Any further insight? Thanks much, in advance!

Ive never done this but you could try using Gpart (as root best to use a live CD) deleting the partitions you dont want then running update grub.
first backup any data you want to keep on an external HDD just incase
goodluck

---

### Post by jamere on 2010-10-27
Halj32,

Thanks again. I've never had occasion to remove previous installs either so I guess I need to do a "risk vs benefit" study.:) You gave me a starting point with the disk utility and I'll definitely look into it.

---

### Post by StephenDavison on 2010-10-27
You can control the behavior of grub2 through it's configuration scripts in /etc/grub.d.  You could disable 30_os-proper by removing the execute permission (sudo chmod ugo-x 30_os-prober), but then you'd want to add chainloader entries to 40_custom for your Windows XP and Windows Vista partitions.  This old thread discusses some of this:
[http://ubuntuforums.org/showthread.php?t=1250838](http://ubuntuforums.org/showthread.php?t=1250838)

There's also a very good grub2 tutorial on these forums:
[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+tutorial](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+tutorial)

---

### Post by jamere on 2010-10-28
StephenDavison,

Thanks much for your reply and links. I'll have a look. I think I'm going to have to look at how to go about removing prior Ubuntu installs. If I can figure out how to do this, the references to them on boot menu list will probably go away. I think its getting to be a "risk vs benefit" question concerning my lack of knowledge in using disk/partitioning utils. :)

---

### Post by jamere on 2010-10-31
A word of warning...NEVER, EVER mess with the Disk Utility, Gparted or GRUB unless you know what in the heck you're doing! I have a dual boot Win XP and Ubuntu 10.10 on an Acer Netbook. I tried removing several older versions of installs to keep them from needlessly showing up on the boot menu. Needless to say I totally hosed GRUB and got the dreaded GRUB Rescue message. Couldn't boot anything! Spent a couple of days poring through Google searches of the Ubuntu forums concerning GRUB problems (on my cell phone). Finally managed to salvage things and fortunately 10.10 was still in tact. Did have to re-build Win XP using the Vista Loader. Hey, I did learn more than I ever wanted to learn about some of intricacies of GRUB, etc. Another bit of advice...download an iso and make a live flash drive (just in case)! :):):)

I'll take my "risk vs benefit" assessment a bit more seriously next time!

---

