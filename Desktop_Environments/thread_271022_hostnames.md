---
title: "hostnames"
date: 2006-10-04
forum: Desktop Environments
---

### Post by OGC on 2006-10-04
Dear all, I am new to ubuntu, but not competelly to linux. I have installed 
ubuntu on one of our servers, and it worked fine up to now; however when I make
sudo whathever
 
it give me this error

sudo: unable to lookup OGC-BioStar via gethostbyname()

I think that this is bnecause I manually edited /etc/hostname, but I am not sure! can you conferm it?

if this is the reason how can I solve this problem as I cannot do sudo or su anymore?

thanks for the help!


Claudio

---

### Post by kerry_s on 2006-10-04
try rebooting so the rest of the files can pick up the new name.

---

### Post by OGC on 2006-10-04
the error stand still. by the way to update the host name I previusly rebooted the system. any other suggestion?

---

### Post by CatKiller on 2006-10-04
> **OGC said:**
> I think that this is bnecause I manually edited /etc/hostname, but I am not sure! can you conferm it?

Yes, that would stop you using sudo. And lots of things. /etc/hostname and /etc/hosts need to agree on what your computer's hostname is. I think that if you use one of the GUI tools it updates both files automatically. You can boot into Recovery Mode, or whatever it's called, and either copy the backup /etc/hostname file back (you did make a backup, right?) or edit your /etc/hosts file to match.

---

### Post by OGC on 2006-10-04
umh.. er.. I did'nt... I see this is the problems, as hosts and hostnames has different name in it, so this is the task to solve... actully I didn't install grub how can I run in recovery mode?

---

### Post by CatKiller on 2006-10-04
I'm in the middle of something at the moment, so I don't fancy a reboot to see where the option is. Might be a GDM session option perhaps? Anyway, you can boot with the live cd, mount your hard drive to /mnt/linux and then ```
gksudo gedit /mnt/linux/etc/hosts
``` if you can't find out how to do it.

---

