---
title: "Desktop effects cannot be enabled with NVIDIA 5200"
date: 2010-05-03
forum: Desktop Environments
---

### Post by jayhawk923 on 2010-05-03
Was running 9.10 and had successfully enabled desktop effects with my NVIDIA GeForce 5200 graphics card... Upgraded to 10.04 and was no longer able to enable the effects. did a clean install and still cannot... 

Have scoured the forums and get a clean run from compiz-check and there are no apparent errors in X log files... 

Really not sure what to check next... any one?

---

### Post by jayhawk923 on 2010-05-03
btw... running 173.14.22 drivers... use of any other version results in errors

---

### Post by dagrump on 2010-05-03
WARNING this could break stuff, but my boxes always get a "sudo nvidia-xconfig" & a reboot as soon as I install the drivers with synaptic, no jockey, & no restricted hardware drivers (or whatever it is).
I haven't had any issues, of course I could just be lucky.
I run 2 boxes with dual cards in SLI so I need a xorg.conf file, or I gain nothing. I've ran lucid since before there was an alpha & it has worked fine. I have no idea why it is acting up for everyone now.
Well, that's my 2 cents, & that about what it's worth.
Good luck.

---

