---
title: "I justy got a new card it;s a Nvidia GF 8800  and I need to know what to do."
date: 2009-05-23
forum: General Help
---

### Post by applefox on 2009-05-23
Ok So my new card is an Nvidia GF 8800 alpha dog edition. The card that I was using when I installed ubuntu was the Nvidia GF 9600. I am wondering what I need to do to have the proper drivers installed. Do I just put it in and have ubuntu get the proper drivers as it restarts like it did the first time or do I need to do this manually? I am a noob so please go easy on me. :) Thanks in advance.

---

### Post by fragos on 2009-05-23
Assuming you're changing cards, power down, swap cards and restart. Ubuntu checks for hardware changes at boot. It's quite possible both cards user the same driver. Do System-> Administration-> Hardware Drivers to see your options.

---

### Post by chriskin on 2009-05-23
i have the 8600 and the 9600 and they both use the same driver, so i will go with what fragos said, all you have to do is put it in, and you are ok. ubuntu will find it and since the driver would be the same, you will just do nothing, everything will just work

now, if there are missing drivers, just install them the usual way :)

---

### Post by random_hypocrisy on 2009-05-23
nVidia's drivers are **UNIFIED**. Any major GeForce card variant above 6200 class will work with the newish drivers (177.xx+).

---

