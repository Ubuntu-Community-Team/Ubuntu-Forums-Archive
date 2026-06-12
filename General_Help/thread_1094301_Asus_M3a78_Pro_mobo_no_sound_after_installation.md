---
title: "Asus M3a78 Pro mobo no sound after installation"
date: 2009-03-12
forum: General Help
---

### Post by Chemical Imbalance on 2009-03-12
Just finished building my new desktop yesterday, and its great!

Asus m3a78 pro mobo
4gb OCZ fatality 1066mhz ram
250gb Seagate Barracuda hdd
Lite-on DVD
Apevia 500W psu
AMD Phenom X4 9500
Cooler Master Elite 335 Case
Building it had just one hiccup (missing some screws)


It runs like butter except for some reason the onboard sound is no longer detected after installation (worked fine in livecd) ???

Here are the specs:[http://usa.asus.com/products.aspx?l1=3&l2=149&l3=639&l4=0&model=2270&modelmenu=1](http://usa.asus.com/products.aspx?l1=3&l2=149&l3=639&l4=0&model=2270&modelmenu=1)

**Can anybody help me out here getting the sound back?**

My appreciation in advance





Oh and here is my integrated soundcard:  nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)

---

### Post by wolfen69 on 2009-03-12
did you right click the volume icon and select "open volume control" to check all the levels?

---

### Post by Chemical Imbalance on 2009-03-12
I upgraded to Jaunty and now it sees my sound device and everything is working.
(btw, the kernel wasn't loading the sound module in intrepid for some reason--maybe a conflict with drivers, i don't know--but the mixer wasn't the problem)


SOLVED--fixed in Jaunty (even with the 180.xx nvidia drivers installed)

oh and the 180 nvidia drivers rock:)

---

