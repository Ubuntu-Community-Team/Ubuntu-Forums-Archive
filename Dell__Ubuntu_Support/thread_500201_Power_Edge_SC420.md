---
title: "Power Edge SC420"
date: 2007-07-13
forum: Dell  Ubuntu Support
---

### Post by Lmeek on 2007-07-13
Hello people. Happy Friday!
Not sure if im in the right category but i have this Power Edge server configured with a RAID1(Mirror)

I had windows 2003 install previously and windows (as it should) didnt konw the difference. 
When I go to install Ubuntu desktop it sees the raid as two seperate drives. 

Any ideas here? Is it a driver issue?

---

### Post by sr20ve on 2007-07-13
What controller are you using? The onboard cerc sata 2s?

---

### Post by Lmeek on 2007-07-13
Yes.

I have rebuilt the raid also just to be sure.

---

### Post by sr20ve on 2007-07-13
As far as I know there is no linux driver that will support that controller in raid mode. You'll need to set the ports to native sata in the bios, then you can configure OS raid if you want.

---

### Post by impactgc on 2007-07-26
Lmeek --

I have the SC420 as well but just the normal 80 GB SATA hard drive.. When I go and try to install Ubuntu it freezes on loading-- while still showing menu.

Did you run into any issues with it freezing up on you?

Thanks,
Adam

---

### Post by bimmerd00d on 2007-07-26
No compiz on that intel gfx card, i just get a white screen with teh i810 driver.

---

