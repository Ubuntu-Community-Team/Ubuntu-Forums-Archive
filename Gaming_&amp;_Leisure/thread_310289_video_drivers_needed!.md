---
title: "video drivers needed!"
date: 2006-12-01
forum: Gaming &amp; Leisure
---

### Post by rkakkar on 2006-12-01
hello all.. i have the gigabyte GA-8GEM800 motherboard using onboard graphics. although ubuntu has detected the card, i think that i am not getting any 3d acceleration out of it because my opengl screen savers are not smooth. i checked their driver page:

[http://www.gigabyte.com.tw/Support/Motherboard/Driver_Model.aspx?ClassValue=Motherboard&ProductID=1835&ProductName=GA-8GEM800](http://www.gigabyte.com.tw/Support/Motherboard/Driver_Model.aspx?ClassValue=Motherboard&ProductID=1835&ProductName=GA-8GEM800)

but there are no drivers for linux. can someone help me? since i want to play Quake 3 on ubuntu.

---

### Post by hikaricore on 2006-12-01
From a terminal type:

```
glxinfo
```

Copy and paste the results here and someone (with this extra information) may be able to help you.  Also the output of:

```
cat /etc/X11/xorg.conf
```

May be helpful to see what driver you're currently using.

Your screen resolution and color depth may also come in handy, and I'm betting this gets moved to the hardware help forum where I don't lurk.  So good luck to ya.

---

### Post by po0f on 2006-12-01
rkakkar,

You need to either use the i810 or i915 driver for that graphics chip.  I don't know how well these chips perform as far as games go, though.

---

### Post by hikaricore on 2006-12-01
I'm presonally using i810 and it works great for an integrated chipset :)

---

### Post by rkakkar on 2006-12-01
okay maybe i should have more faith on ubuntu :D. i ran quake 3 with the default drivers and its running almost as good as it did in windows. however i am not getting any sound :(. any ideas?

---

