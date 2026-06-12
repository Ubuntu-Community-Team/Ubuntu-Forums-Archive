---
title: "[SOLVED] / partition filling up inexplicably"
date: 2009-01-11
forum: General Help
---

### Post by elusivespoon on 2009-01-11
For some reason my root partition getting full and I'm not sure why. I had upgraded some packages and thought something in there was the cause. I realized I had a few old kernels and modules installed I could remove. I freed it up to 75% (of 9.2G) after removing those and thought everything was fine.

Then today, after only doing minor file edits and webbrowsing I'm suddenly back up to 100% usage. The strange thing is, according to `du` I actually have less things on my root partition. (See attached file where every difference but /var shows less disk usage)

Any ideas what is causing this and how I can stop it?

---

### Post by b0b138 on 2009-01-11
Please post output of sudo fdisk -l

---

### Post by elusivespoon on 2009-01-11
> **b0b138 said:**
> Please post output of sudo fdisk -l
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008b1ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9765625   83  Linux
/dev/sda2            1216        1459     1947265+  83  Linux
/dev/sda3            1459       14594   105507933   83  Linux

```

---

### Post by b0b138 on 2009-01-11
oops, and the output of mount

---

### Post by elusivespoon on 2009-01-12
> **b0b138 said:**
> oops, and the output of mount

```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /home type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mosherr2/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mosherr2)

```

---

### Post by b0b138 on 2009-01-12
Try running sudo apt-get clean. (this will remove cached repository items) Do you have a lot of post-install programs installed? Run disk usage analyzer (application>accessories>disk usage analyzer) and "scan filesystem". (also goto edit>preferences and uncheck everything but /) This will give you a nice little interactive pie graph so you can look around for anything that might seems out of place (like a 4 gb dvd copy that accidentily didn't make it to your home)

---

### Post by elusivespoon on 2009-01-12
I already ran `sudo apt-get clean` and checked for out of place files in the Disk Usage Analyzer. Though I suspect it is not just extra packages or a rogue file that is the problem since I had managed to free up a large amount of space which then disappeared without me doing anything to cause a huge file write. Plus the output of `du` suggest I should be using less dispace now, though I'm realizing now du isn't all that accurate.

---

### Post by elusivespoon on 2009-01-12
Ok. Just realizing the reason du was so inaccurate is that I wasn't running it as root. I'm going to narrow my search to those directories a normal user doesn't have permission too.

---

### Post by elusivespoon on 2009-01-12
Problem solved. Kind of. I found out sbackup was somehow backing files up under /media/drive though the external drive wasn't mounted. Though usually it failed at this since the folder didn't exist with no drive mounted. Perhaps I accidently created a folder there. So now I just need to make sure sbackup is working correctly, and that I'm not having a mount problem where folders are left behind after unmounting the device.

EDIT: I'll mark this as solved, and make a new thread if the problem with sbackup continues now that I've deleted the remnant folder under /media

---

