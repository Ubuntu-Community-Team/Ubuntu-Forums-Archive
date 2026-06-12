---
title: "Cannot boot Dell Precision 690 after upgrade to Jaunty"
date: 2009-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fredjoha on 2009-05-21
I have seen other posts about "gave up waiting for root device" when trying to boot Ubuntu 9.04. However, the solution of setting a boot parameter rootdelay=90 does not do anything for me and my Dell Precision 690.

What IS working is booting an earlier kernel, but I don't think I want to keep doing that (now I can't mount any other devices for some reason). Does anybody know the solution to this problem?

The kernel that can't boot is 2.6.27-11. Am I right in assuming this kernel has a big bug in it? Thanks for any help!

---

### Post by pjizz on 2009-05-21
I can't boot to .27-11 either...and when i boot to older kernels of 9.10 it gives a splash screen for intrepid...booting to older kernels also has other random issues.  i haven't heard of a fix yet

---

### Post by fredjoha on 2009-05-22
I gave up on this. Fortunately I've been backing up my home directory nightly to an external disk, so I could make a clean install of 8.04 and restore all my files. I'll stay with this version for some time now...:p

---

### Post by pjizz on 2009-05-25
well i think i am going to have to go clean install, though 8.10 was working fine for me.  so much for being bleeding edge.

out of curiosity and practicality, what was your nightly backup solution?

---

