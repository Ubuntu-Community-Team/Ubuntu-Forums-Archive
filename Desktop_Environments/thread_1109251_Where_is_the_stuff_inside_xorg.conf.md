---
title: "Where is the stuff inside xorg.conf?"
date: 2009-03-28
forum: Desktop Environments
---

### Post by tzcomwiz on 2009-03-28
I'm a Gentoo user but installed ubuntu on my laptop due to its amazing hardware detection. In Gentoo, all the drivers and other specifications for xorg are in /etc/X11/xorg.conf but in ubuntu, there is barely anything in xorg.conf. Where are most of the info located?

Thanks.

---

### Post by hictio on 2009-03-28
Check this: [xorg in Ubuntu 8.04](https://help.ubuntu.com/community/XORGHardy).
Yeap, says "8.04", but applies.

---

### Post by ronocdh on 2009-03-28
> **hictio said:**
> Check this: [xorg in Ubuntu 8.04](https://help.ubuntu.com/community/XORGHardy).
Yeap, says "8.04", but applies.
I have the same question as OP. This link, while informative, seems only to explain that xorg.conf has been drastically simplified. 

Still, the question remains: where *is* the information specified? Even if it's all autodetected these days, it's got to be recorded somewhere. Where?

Also, it should be noted that manually specified values in xorg.conf will still take precedence over unshown autodetected values, as I understand it.

---

### Post by inobe on 2009-03-28
i have been doing a lot of reading, this is real learning

[http://www.x.org/wiki/FAQ](http://www.x.org/wiki/FAQ)

---

### Post by ronocdh on 2009-03-28
> **inobe said:**
> i have been doing a lot of reading, this is real learning

[http://www.x.org/wiki/FAQ](http://www.x.org/wiki/FAQ)
Awesome resource, thank you!

So, basically, the answer I think OP was looking for is that the values X now autodetects can be found in **/var/log/Xorg.0.log**, and can be manually specified (or altered) in xorg.conf.

---

### Post by hictio on 2009-03-28
The values can be over ridden by an entry on '/etc/X11/xorg.conf'; but, take a look at the log file '/etc/X11/xorg.conf' it says that it uses:

```

(==) Using config file: "/etc/X11/xorg.conf"

```

as the configuration file.

Other resources: [X Configuration](https://wiki.ubuntu.com/X/Config), particularly, the part II, [Display resolution configuration](https://wiki.ubuntu.com/X/Config/Resolution).
I wasn't aware that there was an "~/.xprofile" configuration file option as well.

---

