---
title: "growisofs 'Invalid argument' error"
date: 2009-05-23
forum: General Help
---

### Post by blackeye on 2009-05-23
Hi,
New to Linux, first time posting. Running Ubuntu 8.04 on a Dell Studio laptop. Burned one data DVD-RW fine using gnomebaker, then haven't been able to successfully burn another. Tried K3b as well. Been researching it, and have isolated the problem to growisofs. Running it gives this error:

growisofs -speed=1 -Z /dev/dvd=/home/brian/gnomebaker.iso 
Executing 'builtin_dd if=/home/brian/gnomebaker.iso of=/dev/dvd obs=32k seek=0'
/dev/dvd: "Current Write Speed" is 2.0x1352KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=21h/ACQ=02h]: Invalid argument
:-( attempt to re-run with -dvd-compat -dvd-compat to engage DAO or apply full blanking procedure
:-( write failed: Invalid argument

Have found some discussion of this error on the web and in this forum, but nothing it seems that tells me how to fix it!

---

### Post by KhurramM on 2009-05-23
have u tested basero?

have u tried nautilus-burner?

are these two also faulty?

---

### Post by blackeye on 2009-05-24
Tried Brasero, Gnomebaker, and K3b, but no others. It seems that the problemm is with the command that these programs use, grosisofs. Is this not the correct analysis?

---

### Post by blackeye on 2009-06-01
Bump. 
Help? 
Anyone?
Please?

---

### Post by VMC on 2009-06-01
> **blackeye said:**
> Hi,
New to Linux, first time posting. Running Ubuntu 8.04 on a Dell Studio laptop. Burned one data DVD-RW fine using gnomebaker, then haven't been able to successfully burn another. Tried K3b as well. Been researching it, and have isolated the problem to growisofs. Running it gives this error:

growisofs -speed=1 -Z /dev/dvd=/home/brian/gnomebaker.iso 
Executing 'builtin_dd if=/home/brian/gnomebaker.iso of=/dev/dvd obs=32k seek=0'
/dev/dvd: "Current Write Speed" is 2.0x1352KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=21h/ACQ=02h]: Invalid argument
:-( attempt to re-run with -dvd-compat -dvd-compat to engage DAO or apply full blanking procedure
:-( write failed: Invalid argument

Have found some discussion of this error on the web and in this forum, but nothing it seems that tells me how to fix it!

It looks like you were trying to burn that gnomebaker.iso file to the dvd-rw. It tried to erase the -rw but failed.

If that is truly a DVD-RW and not a DVD+RW, that's the problem. I also can't burn DVD-RW discs. Mine are the "yellow" faced Maxell discs. I can using Windows though. I use DVD+RW for Ubuntu.

You might try Brasero again , Launching it from a terminal, like so:
```
brasero --debug &>brasero-debug.txt
```
Then examine that txt file afterwards.
Here's another attempt at reasing dvd-rw:
[http://narnia.cs.ttu.edu/drupal/node/117](http://narnia.cs.ttu.edu/drupal/node/117)

---

