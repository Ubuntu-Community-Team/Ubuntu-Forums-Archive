---
title: "ATI Graphics card problem solved!!!!"
date: 2009-06-17
forum: General Help
---

### Post by cottfcfan on 2009-06-17
With help from the Mint & Compiz forum, i`ve finally resolved the ATI Graphics card problem and hope this can be a help to others.
 If you suffer from delayed boot, screen flicker, Lagging, etc etc, follow these instructions.
 1st remove fglrx driver completely.
 
 2nd Download your ATI driver from the following site:
Follow instructions from manual provided.

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Then Reboot.

Then from a terminal type:
sudo aticonfig --set-pcs-str="DDX,EnableRandr12,FALSE"

Reboot again & Bingo....

No more flicker or lag and increased speed.

---

### Post by alienkid10 on 2009-06-17
delete post please.

---

