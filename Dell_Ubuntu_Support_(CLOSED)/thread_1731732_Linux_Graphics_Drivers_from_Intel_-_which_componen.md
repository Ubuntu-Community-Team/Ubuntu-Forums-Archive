---
title: "Linux Graphics Drivers from Intel - which component?"
date: 2011-04-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Earthsea on 2011-04-17
[SIZE=2]Dear All,

Just installed Ubuntu 10.10 on a DELL Latitude E6520. Everything looks okay but there is clearly a problem with the Intel HD 3000 graphics support. I found the site [www.intellinuxgraphics.org]("http://www.intellinuxgraphics.org") and the page [www.intellinuxgraphics.org/2011Q1.html]("http://www.intellinuxgraphics.org/2011Q1.html") which looks like it will give me what I need... BUT I am new to Linux and am not sure which component I need: 2D driver, 3D driver, Libdrm, Kernel or Libva?

Can someone give me some advice please?

Thanks,
Earthsea
[/SIZE]

---

### Post by mikewhatever on 2011-04-18
Promising as it might look, I really don't think you will benefit from that web site and its downloads. Intel HD 3000 is rather new, so it's not surprising that 10.10 doesn't have good support for it. 11.04, on the other hand, works well, according to reports [-->here<--]("http://ubuntuforums.org/showthread.php?t=1706846").

---

### Post by Earthsea on 2011-04-20
Mike,

Thanks firstly for the opinion on the Intel website. My IT career began 20 years ago on UNIX boxes so moving to Linux on a PC is a kind of a homecoming. I am finding that some of the sites from whom I would have expected better (DELL, INTEL) offer disappointingly weak support. (Actually, to be honest DELL's feebleness is not too surprising: in my experience they have always been very good with h/w support but s/w is a whole different ball game).

Thanks also for the tip about Natty. I had read somewhere that, as you say, it could well be a more promising avenue. We'll see at month end...

Thanks again,
Earthsea

---

### Post by mikewhatever on 2011-04-20
Sorry if my post above may have come across as somewhat condescending, that wasn't the intention. You could upgrade the driver and related packages using one of the PPAs below, first is stable, and second - experimental:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

