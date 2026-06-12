---
title: "Upgrade Intrepid to Jaunty on Inspiron 1545?"
date: 2009-07-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by guitarMan666 on 2009-07-14
My new Dell Inspiron 1545 literally *just* arrived.   It comes preloaded with Ubuntu 8.10 (Intrepid Ibex).  I expected this, however I realized that it has an Intel graphics chip.  My desktop also has a similar Intel chip and using that device with Jaunty (and even Intrepid) breaks 3D acceleration due to a bug in the xf86-video-intel driver.  Has anyone else sucessfully installed Jaunty on a laptop like mine.

In checking the forum, I have found extremely mixed results for different Intel cards so I wanted to ask *before* I try to upgrade, no sense in breaking a perfectly good laptop. :)

The graphics card in the laptop is reported as:
```
$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

Thanks in advance for your advice,

---

### Post by donmatas on 2009-07-23
do you buy your inspiron 1545 with Ubuntu 8.10 preloaded? it is works perfectly?

---

### Post by guitarMan666 on 2009-07-25
Yes I did.  I have upgraded anyway since I posted it and it works fine with some extremely minor issues.  Sound is a little troublesome from time to time particularly with OpenArena but restarting can often fix this and since I don't play that on the laptop often it's a non-issue.

---

