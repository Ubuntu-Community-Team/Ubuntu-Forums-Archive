---
title: "REQ: Please post unmodified &quot;xorg.conf&quot; XML code"
date: 2007-06-19
forum: Desktop Effects &amp; Customization
---

### Post by dkim68 on 2007-06-19
Could someone please post their original unmodified "xorg.conf" plain text file located in /etc/X11

I did not make a backup.

Thanks!

---

### Post by coffeecat on 2007-06-19
Since everyone's xorg.conf is going to be different, I would have thought you'd be better running:

```
sudo dpkg-reconfigure xserver-xorg
```

**Edit:** An even better idea. Boot up the live CD, mount the root partition of your installation with it and then copy the live CD version of xorg.conf to /etc/X11 on your hard drive. That way you'll get a version of xorg.conf tailored to your hardware. And you could copy over those other two system files while you're about it. :)

Er - hate to ask this, but what did you do? :? And why three threads?

---

