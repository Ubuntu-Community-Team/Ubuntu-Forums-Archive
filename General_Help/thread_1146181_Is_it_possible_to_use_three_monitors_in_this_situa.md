---
title: "Is it possible to use three monitors in this situation?"
date: 2009-05-02
forum: General Help
---

### Post by lorderico on 2009-05-02
I have a video card (Radeon 9200 SE) in my PCI slot with two monitors attached to it.  I also also have a monitor attached to the integrated graphics on my PC.  Windows will automatically detect all 3 and can extend the desktop between them.  Ubuntu does not detect the 3rd monitor right now (the one attached to the integrated graphics).  Is there a way for Ubuntu to detect it and stretch the screen between the 3?

Thanks in advance,

Eric

---

### Post by Woody1987 on 2009-05-02
What type of card is the integrated one?

---

### Post by lorderico on 2009-05-02
I think this is it:

*-display UNCLAIMED
             description: Display controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0

That is the result of lshw.  The other two are listed here:

*-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV280 [Radeon 9200 SE]
                vendor: ATI Technologies Inc
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=66 mingnt=8
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 SE] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 4.1
                bus info: pci@0000:05:04.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=66 mingnt=8

Why does the type of integrated graphics matter?

Eric

---

### Post by lorderico on 2009-05-02
Ok, I think the reason that Ubuntu doesn't detect the third monitor is because it is disabled in the BIOS.  When I enable it in the BIOS the second monitor gets disabled.  As far as I can tell, there is no way to have them both enabled at the same time.  However, Windows is able to see all 3 monitors somehow.  Do you how I can Ubuntu to see that third monitor?

Thanks,

Eric

---

### Post by lorderico on 2009-05-03
bump

---

