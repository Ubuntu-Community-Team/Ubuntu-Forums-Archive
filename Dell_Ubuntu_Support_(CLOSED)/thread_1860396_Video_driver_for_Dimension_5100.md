---
title: "Video driver for Dimension 5100"
date: 2011-10-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by savaan on 2011-10-14
I see that it is an Intel GMA950, I just have no clue how to install this thing. I found some intel drivers at [http://intellinuxgraphics.org/user.html](http://intellinuxgraphics.org/user.html) but its not too user friendly to install. I'm still learning Linux :) When I had this comp on 10.10, the driver worked fine. Now that I've upgraded, its like the driver just got deleted. I found a ppa on intellinux, but putting it into my other software and hitting updates gives me this: 

W:Failed to fetch [http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by mikewhatever on 2011-10-15
Can you explain what's the problem exactly. Why do you think you need to manually install the driver? What version of Ubuntu have you upgraded to? What GUI do you use: Unity, Gnome, other???

Intel provides open source drivers for most of its GPUs (gma500 being an exception), so in Ubuntu and other distros, the driver is built into the kernel and should work out of the box.

---

### Post by savaan on 2011-10-30
I recently upgraded to the latest version, 11.10. I'd hoped that it would solve the driver problem, which I first started experiencing in 11.04. My card isn't recognized. I'm not able to change any resolution settings at all and my monitor is no longer recognized as it was on 10.10. This is making it hard to play any of my games (not that its a great gaming card) as the card isn't performing as it should.

I've looked on intellux, my problem with that is that I'm still fairly new to the workings of Linux so compiling a source code is gonna take some step by step instructions

---

