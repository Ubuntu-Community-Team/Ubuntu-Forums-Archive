---
title: "Unique (?) Ipod Problem - ubuntu doesn't see it"
date: 2006-09-07
forum: Desktop Environments
---

### Post by deldredge on 2006-09-07
So I think I have what might be a unique problem getting ubuntu to recognize my ipod shuffle. Following this howto:
[http://www.ubuntuforums.org/showthre...=howto%3A+ipod](http://www.ubuntuforums.org/showthre...=howto%3A+ipod)

I've inserted my shuffle into the usb port and all I get in my dmesg output is this one-liner:

[17180529.652000] usb 1-3: new high speed USB device using ehci_hcd and address 2

Nothing that looks like what it should. No identification, no mount point, etc.
I tried reformatting the ipod in windows to fat32. I tried every USB port on my computer, 1.1 and 2.0. I tried starting up the computer with it already plugged in. I tried my dapper installation and the Edgy live cd.I tried the 386 kernel and the k7 kernel.

The other weird thing is that if I plug the ipod in, then plug a usb drive into another port, ubuntu won't recognize the drive until I pull out the ipod. I've scoured the forums but I don't see anyone with the same problem... It's driving me nuts. Computer is an Athlon XP 1800+ w/ 256mb ram.

Help?

---

### Post by Omnios on 2006-09-07
Nott shure how you are mounting it but found that with the creative zen it has to be mounted with sudo or it will not find the player

---

### Post by deldredge on 2006-09-07
Well, all I'm doing is plugging it in, so, I guess I could say SUDO before I plug it in, but I don't think that would help...:D

---

