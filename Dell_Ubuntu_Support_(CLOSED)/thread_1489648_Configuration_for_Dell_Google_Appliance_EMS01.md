---
title: "Configuration for Dell Google Appliance EMS01"
date: 2010-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by karmic-koala on 2010-05-21
We have an old Google Appliance which dates back to 2007. At the moment its unplugged and is in non production environment.

I am trying to get hold of its configuration without actually breaking the box. Anyone have any idea if the box is x64, how much ram it has, processing power etc?

Its Dell model number is EMS01 but googling for this gives you result for the updated version of the server. I know its got 4x250Gb@7.2RPM SATA drives (can see that from front grill).

---

### Post by portert2202 on 2010-05-26
I ran into one of these appliances today also. It had a Dell serial # on the side that allowed me to get the config details from Dell's support website. 

Don't know if your's is the same as this one but it looks to be a Dell PowerEdge 2950 with two dual core Xeon processors and a bunch of memory

Any idea what the name of this Google appliance is? Or a part # for it?

---

### Post by karmic-koala on 2010-05-28
You're right, its indeed a PowerEdge 2950. Here's an email from Google Enterprise support on how to make the hardware usable again post expiry of contract:


To gain control of the BIOS, you will need to open your appliance to
access a jumper.  Remove the cooling shroud by lifting the release latch
and sliding the shroud toward the front of the system.  The jumpers should
be visible.  They are located adjacent to the RAM slot furthest from the
edge of the motherboard and toward the rear of the chassis, labeled
PWRD_EN and NVRAM_CLR.  You can disable the BIOS password by placing the
PWRD_EN jumper on the two pins closest to the RAM slots.

Ofcourse you'll have to check with Google first before you go messing around with it.

Just for the record its got 2 Xeon x64 processors. Other models vary but ours had 1TB of storage (4x250 GB Sata) and 13 TB of dram.

---

