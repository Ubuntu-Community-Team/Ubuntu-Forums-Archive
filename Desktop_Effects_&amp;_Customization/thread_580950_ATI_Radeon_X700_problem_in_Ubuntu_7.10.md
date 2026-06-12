---
title: "ATI Radeon X700 problem in Ubuntu 7.10"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by Uthen Phutneam on 2007-10-19
I can use it perfectly in 7.04 but after I install 7.10 it cannot use Desktop Effects anymore. Someone help me please :(

---

### Post by hawk88 on 2007-10-19
an bit more info would be usefull.
Wat driver are u using? 
do you have direct rendering? 
```

glxinfo | grep rendering

```

---

### Post by Peter [PSP] on 2007-10-19
Also the same problem for me, and if it counts, i have direct rendering... Not working with the default, nor with the fglrx driver (if I enable the restricted drivers, then upon next boot, there is only a blank screen - known bug, i know...).

---

### Post by Amaranth on 2007-10-19
You card has been blacklisted due to stability issues.

[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

---

### Post by hawk88 on 2007-10-20
If you use the fglrx driver, you also must use Xgl.

have an look here it should help u
[http://ubuntuforums.org/showthread.php?t=488385]("http://ubuntuforums.org/showthread.php?t=488385")

---

### Post by captainskyhawk on 2007-10-26
> **Amaranth said:**
> You card has been blacklisted due to stability issues.

[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

You sure?  According to [this site [techpowerup.com]]("http://www.techpowerup.com/gpudb/") only the X850 used RV480 -- the X700 used RV410.

---

### Post by Amaranth on 2007-10-27
Err, yeah, pretty sure. ;)

That wiki does not have everything we blacklist, it only has what upstream blacklists. I linked to it so you'd know how to work around it. In addition to what that page lists we also blacklist the Mobility X300, X700, and X800.

---

