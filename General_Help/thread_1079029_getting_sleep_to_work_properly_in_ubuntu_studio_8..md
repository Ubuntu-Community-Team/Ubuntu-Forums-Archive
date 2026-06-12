---
title: "getting sleep to work properly in ubuntu studio 8.04"
date: 2009-02-23
forum: General Help
---

### Post by msu3 on 2009-02-23
I've found out that I can't use sleep. It seems like it powers down, but then it seems to turn on as soon as I closed the lid of my laptop. I get a blank screen, ctrl-alt-backspace/delete don't work. 

I tried someone's suggestion to edit the xorg.conf file with VBErestore -"true" but it didn't work. I have a Dell Inspiron 1545 with G45 graphics, though I think when I run "lsmod" it comes up with i915, which I think is for a different Intel chipset? I also included 0:2:0 in the details for the driver listing in xorg.conf, but to no avail.

What I haven't tried yet, though is editing the acpi-support config...mainly because I have a working Ubuntu Studio for recording and I don't want to screw it up.

---

