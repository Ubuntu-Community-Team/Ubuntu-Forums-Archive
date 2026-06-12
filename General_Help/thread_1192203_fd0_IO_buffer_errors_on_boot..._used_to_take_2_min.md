---
title: "fd0 I/O buffer errors on boot... used to take 2 min to boot, now its 45"
date: 2009-06-19
forum: General Help
---

### Post by Elchbulle on 2009-06-19
Hello all, having a very strange issue.  I was running ubuntu 8.14 (intrepid ibex?) and last night decided to do a:

```
sudo apt-get update
sudo apt-get upgrade
```

rebooted fine, came back to terminal and did

```
sudo apt-get dist-upgrade
```

Which appeared to go fine as well, then I rebooted and to my dismay was presented with and endless array of:

```
[ 1699.709869] Buffer I/O error on device fd0p116, logical block 26
[ 1701.698345] end_request: I/O error, dev fd0, sector 216
[ 1701.698353] Buffer I/O error on device fd0p116, logical block 27
[ 1703.685807] end_request: I/O error, dev fd0, sector 224
[ 1703.685814] Buffer I/O error on device fd0p116, logical block 28
[ 1705.674290] end_request: I/O error, dev fd0, sector 232
[ 1705.674298] Buffer I/O error on device fd0p116, logical block 29
[ 1707.661752] end_request: I/O error, dev fd0, sector 240
[ 1707.661759] Buffer I/O error on device fd0p116, logical block 30
[ 1709.650233] end_request: I/O error, dev fd0, sector 248
[ 1709.650240] Buffer I/O error on device fd0p116, logical block 31
[ 1711.637693] end_request: I/O error, dev fd0, sector 256
[ 1711.637700] Buffer I/O error on device fd0p116, logical block 32
[ 1713.622079] end_request: I/O error, dev fd0, sector 264
[ 1713.622086] Buffer I/O error on device fd0p116, logical block 33
[ 1715.609533] end_request: I/O error, dev fd0, sector 272
[ 1715.609540] Buffer I/O error on device fd0p116, logical block 34
[ 1717.593917] end_request: I/O error, dev fd0, sector 280
```

That is just a sampling of what I get, it goes on for 45 minutes straight.  I was completely freaked out thinking I had destroyed my kubuntu installation.  Finally after 45 minutes to an hour it stopped the scrolling messages and came up fine...

I did some googling and found suggestions to add:

```
blacklist floppy
```
and / or
```
blacklist fd0
```

to the /etc/modprobe.d/blacklist  file

Neither of these (or both combined for that matter) make any difference.  

I thought maybe something had changed in my /etc/fstab , checked it and it was the same as before...

The machine appears to be running fine but I can't wait an hour for reboot, even if they are few and far between.

If it's any help, the errors start during the mounting phase, the last thing I see before the scrolling starts is :

```
MOUNTING ZFS                       OK
```


Any ideas on what I can try?  Is there something I need to run after updating my blacklist file to make it take effect?  Obviously something tried reverting back to default when I did the dist-upgrade...

Thanks in advance folks!

Tim G

---

### Post by sdennie on 2009-06-19
Are you using a custom kernel patched with ZFS?  If so, ZFS has large problems with media being removed without being cleanly umounted and is generally unstable on linux.

---

### Post by tgalati4 on 2009-06-19
Pull the power cable from the floppy drive.  It's possible they removed support for it in the latest kernel so it's going crazy!

---

### Post by Elchbulle on 2009-06-20
> **sdennie said:**
> Are you using a custom kernel patched with ZFS?  If so, ZFS has large problems with media being removed without being cleanly umounted and is generally unstable on linux.

Thanks for the replies folks!

I set up ZFS using a forum post here on the ubuntu forums as a guide.  Possibly a custom kernel, but I certainly didn't recompile it or anything when I installed / setup ZFS.  Also I haven't removed any media whatsoever from the machine.  I am not sure if ZFS even has anything to do with the errors it was just the last message that pops up before the errors start scrolling.  The ZFS mount part does say [OK] next to it, so I think that portion of the boot-up is fine.

> Pull the power cable from the floppy drive. It's possible they removed support for it in the latest kernel so it's going crazy! 

I don't have a floppy even installed on the machine which is what makes this problem even stranger!  Maybe I should try throwing one in?  I don't even know if I can find one lying around here...

Thanks for the input folks, anyone else have any ideas?

---

### Post by Elchbulle on 2009-06-22
Anyone have any fresh ideas today?  I think I'm going to try to do a repair installation with a kubuntu disc....

Any thoughts on that?

Thanks!

Tim

---

### Post by Elchbulle on 2009-06-23
Well, I have an update here...

It does appear to be something with ZFS (which in ubuntu is ZFS fuse...)

If I do a CTRL+ALT+DEL once during the errors, they stop and the boot process continues.  When it boots up, I log in, and my ZFS mount point is there, but when I do a ls on it it comes back empty...

So sure enough, somewhere during the mount of the ZFS file system it's kicking out these errors...

Is there an update for fuse, or ZFS for ubuntu?  =\  I guess I will have to move all my data off my 2 TB zfs directory and get rid of ZFS all together =(

Thanks for any input
Tim

---

