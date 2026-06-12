---
title: "Help Installing Graphic Cards Driver Please"
date: 2009-04-11
forum: General Help
---

### Post by Tipped OuT on 2009-04-11
Hi, I have an ATI Mobility Radeon 91000 IGP and I'm using the drivers that came with Ubuntu 8.10 for it. I want to know how to install the official drivers for my graphics card (non open source) because when watching videos it gets really choppy. I'm a noob at Ubuntu (or linux in general) so please be easy. Thanks.

---

### Post by Wayne_V on 2009-04-11
System->Administration->Hardware Drivers

It will show you the proprietary drivers available.

But even with the open source driver video shouldn't be choppy -- what player are you using?  Have you tried different output drivers ('mplayer -vo help' to list them, if that's what you are using).

Just a caution - with the proprietary drivers for ATI compiz will get enabled.  I cannot watch video with compiz enabled.  But I installed compiz-switch to quickly enable/disable compiz and then it works fine ('mplayer -fs -vo xv <video>')

---

### Post by Tipped OuT on 2009-04-11
I have tried that option but no graphic card drivers are displayed. Only my wireless and modem drivers are, which I have already enabled. And I'm talking about videos from youtube etc.

---

### Post by Wayne_V on 2009-04-11
From the driver docs:

ATI Proprietary Linux driver currently supports RADEON 8500 and later, as well as FireGL 8700

If you go direct to ATI, the Mobility Radeon 91000 IGP is not listed:

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Can you download a vid to your system and try playing with different mplayer -vo options to see if one works?  Not sure how to configure flash player video driver options tho -- or if it is even possible.

---

### Post by Tipped OuT on 2009-04-11
> **Wayne_V said:**
> From the driver docs:

ATI Proprietary Linux driver currently supports RADEON 8500 and later, as well as FireGL 8700

If you go direct to ATI, the Mobility Radeon 91000 IGP is not listed:

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Can you download a vid to your system and try playing with different mplayer -vo options to see if one works?  Not sure how to configure flash player video driver options tho -- or if it is even possible.

Actually it is listed. Go to Linux x86 then integrated/motherboard and presto. But the installer doesn't work. It gives out an error and quites. Something about the X-Server.

---

### Post by Wayne_V on 2009-04-11
Yes - I see it there.  But the installer says it only supports up to xorg 7.1.   Not sure what 8.04 was but 8.1 is xorg 7.4:

dpkg --list xorg
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                         Version                      Description
+++-============================-============================-========================================================================
ii  xorg                         1:7.4~5ubuntu3               X.Org X Window System

---

### Post by Tipped OuT on 2009-04-11
Oh. So there's nothing I can do? :(

---

### Post by Wayne_V on 2009-04-11
Probably not.  You might want to review this thread however: [http://ubuntuforums.org/archive/index.php/t-783777.html](http://ubuntuforums.org/archive/index.php/t-783777.html)

I'm assuming since you are using the open source drivers compiz (desktop effects) is off, right?

---

### Post by Tipped OuT on 2009-04-11
Actually no. I have compiz on with full effects. Desktop Cube and everything.

---

### Post by Wayne_V on 2009-04-11
Have you tried turning compiz off to see if video plays smoothly then?

You can install compiz-switch to easily turn compiz off & on whenever you want.

---

