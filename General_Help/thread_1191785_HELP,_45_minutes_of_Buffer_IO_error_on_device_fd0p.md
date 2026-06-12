---
title: "HELP, 45 minutes of: Buffer I/O error on device fd0p116, logical block 26"
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

### Post by Elchbulle on 2009-06-19
bump?  wondering if maybe I posted this question too early in the day for many eyes to see?

---

