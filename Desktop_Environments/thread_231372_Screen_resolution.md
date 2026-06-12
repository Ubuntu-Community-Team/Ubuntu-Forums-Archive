---
title: "Screen resolution"
date: 2006-08-07
forum: Desktop Environments
---

### Post by 4lex on 2006-08-07
How do I adjust it from 1024x768 to 1240x1024?
Som say I should edit the xorg.conf file, but I got no clue how to edit it nor where to find it. I am very new with Ubuntu.

Thank you.

---

### Post by ardchoille on 2006-08-07
> **4lex said:**
> How do I adjust it from 1024x768 to 1240x1024?
Som say I should edit the xorg.conf file, but I got no clue how to edit it nor where to find it. I am very new with Ubuntu.

Thank you.

The best way I have found to edit xorg.conf is to open a term and type:

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by wpshooter on 2006-08-07
IMO, if you don't see that resolution listed under the screen resolution menu (GUI), you should not change to that resolution.  If that resolution is not listed and you think your video card and monitor are capable of displaying at this resolution, you need to find the proper driver for your video card and **THEN** change the resolution on the screen resolution menu.

Good luck.

---

