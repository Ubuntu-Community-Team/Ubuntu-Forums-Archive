---
title: "rsync problems"
date: 2007-02-07
forum: Development CD/DVD Image Testing
---

### Post by grazie on 2007-02-07
Anyone else having problems using rsync? I get the following
```
$ rsync -Lvv --progress rsync://cdimage.ubuntu.com/xubuntu/daily-live/current/feisty-desktop-powerpc.iso .
opening tcp connection to cdimage.ubuntu.com port 873
opening connection using --server --sender -vvL . xubuntu/daily-live/current/feisty-desktop-powerpc.iso 
@ERROR: Unknown module 'xubuntu'
rsync error: error starting client-server protocol (code 5) at main.c(1296) [receiver=2.6.8]
```

---

### Post by UBfusion on 2007-02-07
Getting amd64 desktop as I write using windows rsync, no problems. 

Perhaps it's server overload (all ubuntu sites are overloaded due to the overwhelming success of Herd3....)

Just keep trying

---

### Post by spd106 on 2007-02-07
Try ```
rsync -Lvv --progress rsync://cdimage.ubuntu.com/[COLOR="Red"]cdimage/[/COLOR]xubuntu/daily-live/current/feisty-desktop-powerpc.iso .
```

---

### Post by grazie on 2007-02-07
Thanks for highlighting my obvious error, spd106. All is working fine now.

However it does seem a bit odd to have a cdimage subdomain and then have cdimage in the source tree. Also, it means the http and rsync servers are set up differently. And finally it's not the same as what's described in the [documentation]("https://help.ubuntu.com/community/RsyncCdImage"). A little consistency would be good.):P

---

### Post by ShadowDragon on 2008-01-16
> **grazie said:**
>  [...] Also, it means the http and rsync servers are set up differently. [...]
Nope, they are the same, only difference is that if you drop out /cdimage the http-server still understands what you are trying, the rsync doesn't.
You can try, http:// works with or without /cdimage

> **grazie said:**
>  [...] And finally it's not the same as what's described in the [documentation]("https://help.ubuntu.com/community/RsyncCdImage"). A little consistency would be good.):P
I have updated the documentation. ;)

---

