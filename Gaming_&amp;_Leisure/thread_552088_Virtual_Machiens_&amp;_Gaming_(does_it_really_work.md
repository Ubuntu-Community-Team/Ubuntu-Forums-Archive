---
title: "Virtual Machiens &amp; Gaming (does it really work?)"
date: 2007-09-16
forum: Gaming &amp; Leisure
---

### Post by MozartlovesUbun2 on 2007-09-16
this post below mentions it's possible to play games inside a virtual machine where host is linux and the guest VM is windows.

[http://ubuntuforums.org/showthread.php?p=3372838#post3372838](http://ubuntuforums.org/showthread.php?p=3372838#post3372838)

question:
is it possible to play 3D games? (i thought a VM OS doesn't have direct access to the graphic card)

thanks

---

### Post by rejser on 2007-09-16
That's true, It don't have access to the graphics card. So maybe Minesweeper, but hardly anything that demands gpu.

---

### Post by MozartlovesUbun2 on 2007-09-16
> **rejser said:**
> That's true, It don't have access to the graphics card. So maybe Minesweeper, but hardly anything that demands gpu.

LOL

by the way there is a linux version of minesweeper too.

---

### Post by Ferrat on 2007-09-16
> **MozartlovesUbun2 said:**
> LOL

by the way there is a linux version of minesweeper too.

They are working with getting 3D support to VMs but it's only exprimental and not very good.

---

### Post by MozartlovesUbun2 on 2007-09-16
> **Ferrat said:**
> They are working with getting 3D support to VMs but it's only exprimental and not very good.

If that's true I'm up for testing it! :)   Just wondering why the graphics part is taking so much longer when everything else works so well in a VM (personally I've so far only used VMWare)

---

### Post by hikaricore on 2007-09-16
No it does not work.

---

### Post by MozartlovesUbun2 on 2007-09-16
(found this with a google search)

Video: Windows games running in full 3D on Mac OS with VMware Fusion

[http://digg.com/lbv.php?id=1326735&ord=1](http://digg.com/lbv.php?id=1326735&ord=1)

Quote:
VMware products have had a semi-hidden switch for some sort of 3D support in virtual machines on Linux and Windows since VMware Workstation 5.0, which was released almost 2 years ago (April 2005).

Since then, work on the 3D front has been progressing steadily, with DirectX 8.1 support in VMware Workstation 6 and VMware Fusion (both are built from the same code base).

---

### Post by KhaaL on 2007-09-16
True, but they dosen't seem to have progressed beyond dx8.1 for a long time... Dosen't seem to be a priority feature.

---

### Post by splintercellguy on 2007-09-16
No, too slow, and too expensive, since resources are wasted virtualizing the hardware instead of simply using an API wrapper like Wine.

---

### Post by Dimitriid on 2007-09-16
2d does work great however. I use it for Ultima Online for a couple of reasons
a) vmware player is just  FAST, way faster than in whine which is important
b) Wine cannot run the patch utility, and patching over windows then trying on Linux makes the game unplayable. Patching is required for me
c) Many programs for non EA servers are made by some very bad and very lazy "developers" using things like IE 6.0 ( and it just crashes if it doesnt detects IE instead of letting you use mozilla engine on wine ) or .net 2.0 framework :( 

So even if i manage to code all the tools I need for my favorite server and even if I get to patch the client and get it to work on wine ( unlikely ) I would still need to do something about the vast speed improvement on wvmare. In fact the game just flat out locks on wine where there is too many items on screen/server tries to load too many items ( UO is a really badly programmed game ( or at least very outdated ) that loads all items from server as soon as you walk within "range" even if those items are locked away in containers inside players houses )

So vmware does has its uses for gaming....on 2d.

---

