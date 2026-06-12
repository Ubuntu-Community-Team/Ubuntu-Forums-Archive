---
title: "Quake 4 on Xubuntu 11.04 x86_64"
date: 2011-10-02
forum: Gaming &amp; Leisure
---

### Post by kn0w-b1nary on 2011-10-02
Hey all,

I have a 64 bit Xubuntu 11.04 installation I'm trying to get quake 4 on.

I ran the installer and copied over the .pk4's. I'm having this error though: ```
Sys_Error: Texture compression unavailable
```

Any help? I have included output of "glxinfo" and "quake4"

Thx in advance!

---

### Post by Toz on 2011-10-08
You appear to have an Xpress 200 card (RS482 chipset). ATi dropped support for this card sometime back (see: [http://wiki.cchtml.com/index.php/Hardware]("http://wiki.cchtml.com/index.php/Hardware")) and as a result, there is no proprietary driver available for your card (meaning no texture compression - possibly). 

Your only option is to use the opensource radeon driver. However, according to: [http://www.x.org/wiki/RadeonFeature]("http://www.x.org/wiki/RadeonFeature") st3c compression is complete via **libtxc_dxtn.so**.

A quick search for libtxc_dxtn.so has found that it is available from xorg-edgers ([http://www.ubuntuupdates.org/packages/show/309632]("http://www.ubuntuupdates.org/packages/show/309632")) and [http://www.ubuntuupdates.org/ppa/xorg-edgers?dist=natty]("http://www.ubuntuupdates.org/ppa/xorg-edgers?dist=natty").

---

### Post by SeaHawk22 on 2011-10-08
I was just looking to install quake 3 as an old throw back, but I cannot find my quake 3 disk.... Nor could I find any sites that have the Linux version, to purchase of course.

---

### Post by kn0w-b1nary on 2011-10-09
> **SeaHawk22 said:**
> I was just looking to install quake 3 as an old throw back, but I cannot find my quake 3 disk.... Nor could I find any sites that have the Linux version, to purchase of course.

Check out Openarena. Almost exactly the same.

I've lost access to the box I had, (my mom wanted it back) so I am unable to work any more on it at the moment. :/

---

### Post by hollowsyndicate on 2011-10-09
libtxc_dxtn.so fixed quake 4 on my intel graphics. i had 2 compile it in 10.04 tho, xorg edgers dont have a 10.04 deb :(

---

### Post by mastablasta on 2011-10-13
> **hollowsyndicate said:**
> libtxc_dxtn.so fixed quake 4 on my intel graphics. i had 2 compile it in 10.04 tho, xorg edgers dont have a 10.04 deb :(
 
 
i believe there s a PPA available for 10.04.

---

### Post by Elysius on 2011-10-13
How does Q4 perform at all under ubuntu? Really curious...still have the Q3 Arena CD laying around somewhere.

---

### Post by Toz on 2011-10-13
Q4 performs well here (Compaq 8510p notebook, 4GB ram, ATI HD2600 with proprietary drivers). Strogg carcases everywhere.

---

