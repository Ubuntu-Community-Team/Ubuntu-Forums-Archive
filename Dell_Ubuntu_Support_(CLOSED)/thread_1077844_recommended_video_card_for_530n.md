---
title: "recommended video card for 530n"
date: 2009-02-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by timebomb on 2009-02-22
The price of the 530n is pretty attractive at the moment for the features and price - Dual Core E5200 (2.5GHz,800FSB), 2GB RAM, 320GB HD, 19" monitor - for $428! I'd do some upgrading, later, esp. on RAM and as it has a integrated graphics chip (Intel Graphics Media Accelerator 3100). 

What would folks here recommend for a graphics card, keeping in mind price (under $200, well, $150) and compatibility?

Thanks.

---

### Post by gbrainin on 2009-02-22
This is totally unscientific, but I believe I've seen fewer people complaining about problems with nVidia cards than ATI ones.  However, both brands generally work.

If you're buying a card separately from the computer purchase, I would check the hardware database first.  From what I've seen, most cards will work, but if the model number isn't in the database yet, it won't be autodetected.

---

### Post by notwen on 2009-02-23
I've got a 530n and I installed a Nvidia Geforce9600 GT w/o any issue, the install picked it up and everything.

---EDIT---
Just a FYI, most cards will likely overlap the SATA connectors on the mobo and you'll probably have to re-arrange your SATA connectors or either purchase some low-profile SATA cables.  =]

---

### Post by timebomb on 2009-02-23
Thanks. That is really helpful. I was looking that card already.

---

### Post by occams_beard on 2009-02-24
> **notwen said:**
> I've got a 530n and I installed a Nvidia Geforce9600 GT w/o any issue, the install picked it up and everything.


Did you upgrade the PSU?  AFAIK, the stock PSU in a 530n is only 300 watts. That would really be cutting it close I think with a 9600gt. 

I do know the quad core Inspiron 530 comes with a 350 watt, which would likely be OK, but the dual cores only come with a 300 watt... I would probably upgrade the PSU before going with that card.

---

### Post by timebomb on 2009-02-24
> **occams_beard said:**
> 
I do know the quad core Inspiron 530 comes with a 350 watt, which would likely be OK, but the dual cores only come with a 300 watt... I would probably upgrade the PSU before going with that card.

Appears to come with a 300 watt, so I should might back shift on the card. One of the 9400GTs would probably work.

I found this link helpful - someone who clearly had the same idea a few months ahead of me:

[http://www.humans-enabled.com/2008/11/dell-inspiron-530n-nvidia-9400gt-ubuntu.html](http://www.humans-enabled.com/2008/11/dell-inspiron-530n-nvidia-9400gt-ubuntu.html)

---

### Post by notwen on 2009-02-24
> **occams_beard said:**
> Did you upgrade the PSU?  AFAIK, the stock PSU in a 530n is only 300 watts. That would really be cutting it close I think with a 9600gt. 

I do know the quad core Inspiron 530 comes with a 350 watt, which would likely be OK, but the dual cores only come with a 300 watt... I would probably upgrade the PSU before going with that card.

I was curious about this as well, but after some research and even contacting a Dell CSR I was told that the quad core 530 shipped w/ a slightly larger PSU and I did go w/ the Inspiron 530 w/ the Quad Core.

This quote from Wiki is what made me question a Dell CSR:
> **Compatibility Note: There are actually two versions of the Inspiron 530 in production, which are not differentiated in their specifications. When ordered with an Intel Q6600 Core 2 Quad processor, the 530 is equipped with a FoxConn G33m03 motherboard and a LiteOn 375W power supply. When ordered in any other configuration, the 530 is typically equipped with a FoxConn G33m02 motherboard and a 300W Bestec power supply.** The G33m02 and G33m03 are essentially identical except for the power regulation section of the motherboard. Essentially, the G33m02 is a depopulated (cheaper) version of the board which only has 6 voltage regulator IC's as opposed to the 11 voltage regulators on the G33m03. In practice, this means that the G33m02 version of the motherboard is physically incapable of providing enough current to operate the Intel Q6600 CPU. In essence, if you do not order the Quad Core processor with the system initially, you will NOT be able to upgrade it to one later.

---

### Post by happycube on 2009-02-25
Aside:  The depopulated G33 board might have a chance at running a Q8200 at least, which uses considerably less power than the Q6600.  Although if the power circuits can't handle the amperage... 

I'd just take the Q6600 upgrade for $50 myself and get the upgraded components.

(What I actually bought?  A studio 540 scratch+dent with a Q8200 - I was lucky and it was $349+T/S.  Then I added a 4830 for $105 off 'egg - nvidia is probably better ATM, but by 10.04 there ought to be open 4xxx 3D drivers, and I've got a ram upgrade on the way...)

---

### Post by timebomb on 2009-03-01
Update - I bought the 530n as I described above and a 9400 GT/512MB. I wiped the HD and installed 8.10. Everything works terrific thus far. For just under $500 I am a pretty happy camper.

---

