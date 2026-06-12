---
title: "garbled display"
date: 2011-09-10
forum: Desktop Environments
---

### Post by Bynw on 2011-09-10
From time to time. Generally when switching users or going from something running full screen and then off of full screen. The display of the desktop is garbled. Images, icons, letters. Everything, even the menus.

I am running Ubuntu 11.04 in Classic mode.

I have attached a screenshot and any help to diagnose this and fix it would be greatly appreciated. Thanks.

---

### Post by Krytarik on 2011-09-10
It seems like an issue with the video driver, so try another one, generally spoken. :D

Please provide more - actually *any* - details in the regard if you can't fix it on your own.

Greetings.

---

### Post by Bynw on 2011-09-10
whats the quickest way of getting the info?

---

### Post by madjr on 2011-09-10
looks like the force is weak on you

---

### Post by Krytarik on 2011-09-10
> **madjr said:**
> looks like the force is weak on you
LOL:D What does this mean in that regard?

No, seriously, how about this!?:
```
lshw -c video
```

---

### Post by madjr on 2011-09-10
check the pic :p

---

### Post by Krytarik on 2011-09-10
> **madjr said:**
> check the pic :p
Yeah, true. Already had forgot about this. :D

---

### Post by mowriter on 2012-08-23
> **Krytarik said:**
> LOL:D What does this mean in that regard?

No, seriously, how about this!?:
```
lshw -c video
```

I have exactly this same problem, now in Ubuntu 12.04, also running an older Dell (Dimension E310)

Running the lshw -c video command resulted in the following:

WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 82915G/GV/910GL Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:dff80000-dfffffff ioport:ecd8(size=8 ) memory:c0000000-cfffffff memory:dff40000-dff7ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


Any help on this would be appreciated.  I too find it frustrating.  Will likely get a new video card, btw, but want to know if anything else is relevant.

---

