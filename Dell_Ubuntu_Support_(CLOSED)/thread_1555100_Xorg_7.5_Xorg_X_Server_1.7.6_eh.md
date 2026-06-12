---
title: "Xorg 7.5? Xorg X Server 1.7.6? eh?"
date: 2010-08-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kamohammed on 2010-08-17
ok... Related to my graphics problems and drivers... I discovered that the catalyst and drivers requires Xorg version 6.7 to 7.5 (where 7.5 is currently the latest and 7.6 coming out soon...).

When i did X - Version
and
man xorg | grep xorg-server

I get that i have Xorg-server 1.7.6
(along with X Version 11, and Xorg(1))

So... I am confused. I read some where (Forgive copy and paste)

-------
> In short, X.Org != X.Org *server*. The X.Org is "protocol version  11, release
> 7.5", which contains (among other things) the  server, version 1.7.6. The catch
> is that the actual server  executable is also called Xorg. ;-)
-------

So... I am qualified to install the drivers? And either way when I do, my pc dont boot and i have the Hold shift and go to safe mode etc...

Thanks for assistance

*just info:
Dell Studio 1535
Ubuntu 10.04
*

---

### Post by silverglade00 on 2010-08-18
> **kamohammed said:**
> ok... <snip>catalyst and drivers requires Xorg version 6.7 to **7.5** <snip>

The X.Org is "protocol version  11,** release 7.5**"


Looks like you should be good to go.

---

### Post by kamohammed on 2010-08-20
hmm... 
then why when i install the drivers (as instructed) i cant boot after (because of bad graphics drivers)... ?

anyways. I think its something else causing the problem... Will try installing drivers again via a different approach...

---

### Post by silverglade00 on 2010-08-20
You should be able to go into System - Administration - Hardware Drivers and have it install the correct drivers for you.

---

### Post by kamohammed on 2010-08-26
> **silverglade00 said:**
> You should be able to go into System - Administration - Hardware Drivers and have it install the correct drivers for you.

Yeah that seems to work...

I un-installed everything ATi, and ran the Hardware Drivers under System -> Administration. It detected a proprietary driver something something something... Installed that, rebooted and it seems to be working...

I did a little test. I ran Lineage2, and the graphics didnt lag 1fps like before.
Once before I had a problem where textures use to get messed up severely... didnt see that happening as yet... but so far... it works...

---

