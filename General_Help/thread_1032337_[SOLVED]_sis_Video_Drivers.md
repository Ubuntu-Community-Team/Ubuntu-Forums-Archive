---
title: "[SOLVED] sis Video Drivers"
date: 2009-01-06
forum: General Help
---

### Post by ricardo_78 on 2009-01-06
Newbie getting there.

I have a motherboard with a sis chipset which keeps booting gnome 800 x 600....

I have realised that not all is well from the output of lshw below. 

```
       *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: cap_list
                configuration: latency=0

```

However, I can quite work out what I need to do.  I found xorg drivers xf86-video-sis-0.10.1 but am somewhat confused as to how I might load this.

I have googled and allot is covered.

Push comes to shove I'll get a video card but would prefer to get it sorted.... before that!

Thanks in advance.....

---

### Post by birddog165 on 2009-01-06
hmmm. I hate to be this guy, but you're not the first person I've heard complaining about sis video chips. It might be more work to fix this, unless someone else knows what to do, I'd get a new card. If you do get a new card, go with nVidia.

---

### Post by ricardo_78 on 2009-01-06
Indeed I think you have a point.....

---

### Post by birddog165 on 2009-01-06
I'm really sorry for being a poor help, but I wish you the best of luck in your search for a solution.

You could also check if this helps:
[http://ubuntuforums.org/showthread.php?t=994195&highlight=sis+800x600]("http://ubuntuforums.org/showthread.php?t=994195&highlight=sis+800x600")

---

### Post by ricardo_78 on 2009-01-07
No probs... I bought a cheapish Nvidia card (27 GBP) and all is working well.  I am mightily impressed with this linux experiment!!!!

---

