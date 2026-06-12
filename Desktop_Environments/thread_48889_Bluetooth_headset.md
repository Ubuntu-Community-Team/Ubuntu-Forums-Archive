---
title: "Bluetooth headset"
date: 2005-07-14
forum: Desktop Environments
---

### Post by Terracotta on 2005-07-14
Hy, I've bought a bluetooth headset, I already have a bluetooth dongle (d-link dbt120), and I was wondering, is it difficult to get such a headset working with skype in linux? in windows it's a PIA :), and then to imagine that I expected a lot of work to get it working in linux so I decided to install windows for a while since I don't have much time. The most people I've seen on the internet who had it working in linux used gentoo, and euhm well I'm not quite ready for that OS. I've had kubuntu installed several times and I liked it very much. Has anyone here tried it?.
Greetz.

---

### Post by kaiesh on 2005-07-15
Just so you know you're not alone in this, I'm trying to mess around with it too. I have a Logitech MX900 mouse, and it comes with a usb bluetooth base station. I'm migrating away from Windows to Ubuntu, and have been using my headset with Widcomm in Windows without any trouble.

I've managed to get the bluetooth mouse working, but I don't know exactly what's needed (in terms of modules) to get bluetooth support for audio... (also if anyone knows how to get Ubuntu to dump to terminal the devices and their MACs which are in range of the base station, this would also be useful)

So if anyone does have any idea on how to do this, please enlighten!

Cheers,
Kaiesh

---

### Post by kaiesh on 2005-07-15
[QUOTE=kaiesh](also if anyone knows how to get Ubuntu to dump to terminal the devices and their MACs which are in range of the base station, this would also be useful)[/QUOTE]

Just for anyone else's future reference, the command for this is:

```
hcitool scan
``` 

It assumes you have your bluetooth dongle/base-station set up.

Kaiesh

---

### Post by KriC on 2005-07-15
Hi guys,
i got a problem with BT too.
some days ago i bought my BT/USB and i wanted to make it works with linux.
I also followed gentoo forums; i was wondering if that procedure would works even on my kubuntu machine:
Conclusion: i got it all working until i try to compile a file called obexserver.c. Kubuntu doesn't compile it.
If I can't compile that file i also can't make ussp-push works 'n' can't transfer stuff on my mobile.
My BT/USB works, 'cause if i type hcitool scan, it see my mobile, I also make a new node with mknod on /dev/rfcomm0 and everything works perfectly, but it won't compile a stupid file .c

hoping someone would be so mercy to answer me
and sorry for my bad english, but it is not my first language

Greetz   ;-)


KriC

---

### Post by kaiesh on 2005-08-05
Just so people know there is a discussion going on about bt headsets at:
[http://ubuntuforums.org/showthread.php?p=288856](http://ubuntuforums.org/showthread.php?p=288856) 
as well. So you may like to look there to post/read.

Cheers,
K

---

