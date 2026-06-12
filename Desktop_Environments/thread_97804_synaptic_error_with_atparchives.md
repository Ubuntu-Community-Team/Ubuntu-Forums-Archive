---
title: "synaptic error with atp/archives?"
date: 2005-12-01
forum: Desktop Environments
---

### Post by ren wins on 2005-12-01
i was trying to install a couple packages with synaptic
when i get this error

> E: /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb: subprocess pre-installation script returned error exit status 1

it happend while the changes were being applied
there's more in the terminal of the 'changes applied' window
but i cant figure out how to copy/paste those

should i be worried?

---

### Post by Xian on 2005-12-01
This should fix your issue:

$ sudo apt-get install tetex-bin

---

