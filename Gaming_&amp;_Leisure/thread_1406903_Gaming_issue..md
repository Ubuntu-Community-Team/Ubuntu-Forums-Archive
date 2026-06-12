---
title: "Gaming issue."
date: 2010-02-14
forum: Gaming &amp; Leisure
---

### Post by lockalidiot on 2010-02-14
I've been having this issue for three days now. It is involved with gaming. I play a while, say, Open Arena, and then my display goes black except for a blue notification that says "no signal detected". Whats whit that? My cpu-specs can easily run all the games I have.

I ran this, so that you can see if there is anything that isn't supported or something.
```
me@here:~$ sudo lshw -C display

*-display               
       description: VGA compatible controller
       product: GT200 [GeForce GT 220]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fd000000-fdffffff memory:d0000000-dfffffff(prefetchable) memory:ce000000-
cfffffff(prefetchable) ioport:d800(size=128) memory:fe980000-
fe9fffff(prefetchable)
```

Please give the answer like you would to a complete idiot, so I will actually understand it.

---

### Post by portets on 2010-02-14
i'd say your monitor is going bad. but only if you have a CRT monitor.(like a tv)

or do you have an LCD?

edit:

```
clock: 33MHz
```

wait, that doesn't sound right at all..... shouldn't that be like 600mhz?

---

### Post by lockalidiot on 2010-02-14
> 
```
clock: 33MHz
```
wait, that doesn't sound right at all..... shouldn't that be like 600mhz?

Beats me, no idea!

Display, not one of those TV type things, no. BenQ FP92E, so yes it's an LCD(at least it's flat...).

EDIT: It seems that my core temp get's up pretty easily... Could it be that? I rotated my desktop cube for a moment just to test the effect. It made the temp to go from my average of 76C to 85C... the slow down threshold appears to be 255C... According to nVIDIA..

---

### Post by portets on 2010-02-14
yeah, that's a bit warm. and the threshold should be 105C....

i don't know, i think you should wait for someone else to come here

---

### Post by lockalidiot on 2010-02-15
I think that one thing I'm going to do about it, is to open this box up and see just how dusty the bugger is... Might be that the fan doesn't work properly cause it is so covered in dust...

---

### Post by Tikkyca on 2010-02-15
I think you need to update your driver.

---

### Post by lockalidiot on 2010-02-15
Ok, how do I do that, or rather, from synaptic, software center or nVIDIA homesite?

---

### Post by lockalidiot on 2010-02-15
Ok, done that, works better. Thank you all!

---

