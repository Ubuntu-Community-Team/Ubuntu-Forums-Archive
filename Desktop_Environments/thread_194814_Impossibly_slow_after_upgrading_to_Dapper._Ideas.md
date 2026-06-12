---
title: "Impossibly slow after upgrading to Dapper. Ideas?"
date: 2006-06-12
forum: Desktop Environments
---

### Post by coe on 2006-06-12
Hi,

First of all, I apologize for not having a concrete problem description -- I realize this does not give you guys much to work with, but anyways,

I upgraded successfully to Dapper on three breezy machines by now, and everything went fine. My home PC though has become a total, unbelievable slug.
opening a folder in nautilus takes seconds, scrolling a webpage in firefox is horribly slow, I can't see any movies anymore, even small ones, the frame rate is so low and jerky that it's just not possible.
I didn't get these problems with the other PC's so I'm sure something must be wrong with the config on this one (which is comforting, well, ...somehow). I just don't have any idea where to start looking... I searched the forums but couldn't find anything similar.
I checked the device manager and it says "device: unknown / vendor: unknown" for pretty much every entry, but I don't know if this is at all related.
At this point I'll take any wild guess you may have...

thanks in advance,
coe

---

### Post by Wyrm_1972 on 2006-06-12
Did you upgrade or do a full install?

What are the stats on your current machine?

---

### Post by coe on 2006-06-12
I upgraded from ubuntu breezy.
In attachment I included some system specs. 
thanks for the help,
coe.

---

### Post by darkpark on 2006-06-12
[QUOTE=coe]I upgraded from ubuntu breezy.
In attachment I included some system specs. 
thanks for the help,
coe.[/QUOTE]

Can you post a copy of xorg.conf?   It could be the video driver.

---

### Post by coe on 2006-06-12
Here you go.
coe

---

### Post by dglock on 2006-06-12
Check your hard drive to be sure dma is turned on. as root, hdparm /dev/hdx   put in your drive letter in place of the x.

 don

---

### Post by coe on 2006-06-12
dma seems to be on, don.
thanks though.
coe.

---

### Post by coe on 2006-06-14
Would it help to recompile the kernel? I have this nagging feeling it's just some silly setting in a configuration file somewhere, and it's driving me nuts ... aaargh.
(help)
coe

---

