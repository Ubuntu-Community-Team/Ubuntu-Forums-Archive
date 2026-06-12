---
title: "Tried to change host name and bunged up X org somehow"
date: 2006-09-29
forum: Desktop Environments
---

### Post by bignose on 2006-09-29
So, I wanted to change my hostname, so I did a 

sudo hostname zim

This fudged things up such that sudo couldn't call gethostbyname any more, because I had not changed /etc/hosts , makes sense.

So I restarted to single user mode [recovery mode] and changed hosts and /etc/hostname and ran hostnname [last step likly not necessary]

Then i rebooted. When i did, the machine comes up fine but my monitor says "Out of frequency range". This confused the heck out of me as I didn't touch my xorg.conf file at all.

Soooo I went in an reversed the changes I made and went back to the first hostname, rebooted and still no Xorg..

Can anyone shed some light on this ? I can ssh in and do work on the machine no problem, so that's not an issue, I'd just like X to work again.

Thanks.

---

### Post by bignose on 2006-09-29
um.. ignore me. this was all user error.

---

