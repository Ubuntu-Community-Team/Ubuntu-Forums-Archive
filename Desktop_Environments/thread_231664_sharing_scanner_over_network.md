---
title: "sharing scanner over network"
date: 2006-08-07
forum: Desktop Environments
---

### Post by boast on 2006-08-07
Can someone link me to a tutorial or show me how to setup my scanner to share through my network?

---

### Post by llamakc on 2006-08-07
What sort of scanner is it? 
What's the brand/model?
How is it connected to your machine?

I used the hp-makeuri command to get mine recognized by SANE: it's an HP all-in-one fax/copier/scanner that is connected via ethernet to my network router.

When I'm hunting a howto for Ubuntu I make my way to [http://wiki.ubuntu.com](http://wiki.ubuntu.com) and use the "search" function. 

I found this: [https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

---

### Post by boast on 2006-08-07
Its a Hp  3400c- it's supported by sane. I was trying to setup saned but it was too confusing.

---

### Post by llamakc on 2006-08-07
What about the other questions I asked? How is it connected to your computer?

Oh, and have you installed the hplip package yet? That provides the hp-toolbox frontend. My printer's connected over the network and I had to do:

```

root@dothan:/home/ken# hp-makeuri 192.168.0.102

 HP Linux Imaging and Printing System (ver. 0.9.7)
 Device URI Creation Utility ver. 2.5

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.
root@dothan:/home/ken# hp-makeuri 192.168.0.102

 HP Linux Imaging and Printing System (ver. 0.9.7)
 Device URI Creation Utility ver. 2.5

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

 Creating URIs for '192.168.0.102':
CUPS URI: hp:/net/Officejet_7200_series?ip=192.168.0.102
SANE URI: hpaio:/net/Officejet_7200_series?ip=192.168.0.102

```

And I added it as a HP/Jetdirect printer using the first CUPS line from above as the path (editing out where it prefills with 'socket'). Finished up with choosing the printer model and driver and that was all.

I did have to reboot for SANE to work but that could have just been due to my aloofness.
 Creating URIs for '192.168.0.102':
CUPS URI: hp:/net/Officejet_7200_series?ip=192.168.0.102
SANE URI: hpaio:/net/Officejet_7200_series?ip=192.168.0.102

---

### Post by boast on 2006-08-08
oh, um. 

What sort of scanner is it? [b]Scanjet
What's the brand/model? HP/3400c
How is it connected to your machine? USB
----
I was looking how one could share a scanner over network, and saw saned. So I installed it, and tried it, but in the end I have two installations of saned, and I don't know how to remove it. And I kept getting it could not detect any usb scanners, and I had no idea how to add it on the config or w/e.

---

