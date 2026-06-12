---
title: "Almost there with network, but..."
date: 2006-03-20
forum: Desktop Environments
---

### Post by s1mple_M4N on 2006-03-20
Hi all - I've learned so much in the last few days from these forums and the wikis, and am enjoying Ubuntu, but one thing still frustrates me - in windoze it's real easy to 'map' a network drive so it acts as a permanent drive on my machine. I have followed instructions about installing samba, editing fstab, etc and have come so close but still not able to see network drives with OpenOffice.org or media apps.

I am constantly getting the following error in terminal when I sudo mount -a - tree connect failed ERRDOS - ERRnosuchshare (You specified an invalid sharename).

I have a feeling that it may be the winblows share itself - the folder I am sharing is on the D:/ drive (//192.168.0.1/Media/Our Music). Is it possible that the space in 'Our Music' is causing the problem? If so - how do I correct that in /etc/fstab?

Any help appreciated.

RoyJ

---

### Post by mwaddoups on 2006-03-20
Try changing it in fstab to //192.168.0.1/Media/Our\ Music/ - this should symbolise a space.

---

### Post by Jason_25 on 2006-03-20
Isn't that what places > connect to server does?

---

### Post by Dragineez on 2006-03-20
> Isn't that what places > connect to server does?Yes, but it's not permanent. He wants the network share auto-mounted at every boot. mwaddoups is correct, the problem is the space in the file/directory name - one of my own pet peeves. His solution should solve the problem.

---

