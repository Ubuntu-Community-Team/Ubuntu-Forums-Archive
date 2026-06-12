---
title: "Blank screen"
date: 2009-03-05
forum: General Help
---

### Post by fknyeah on 2009-03-05
Turned on my Laptop this morning, everything seemed ok until the boot menu finished loading.  At the point when there should be a sign in screen, the monitor goes blank.  It is still on, just black.

Please help.

---

### Post by abhilashm86 on 2009-03-05
i guess your system must be in command mode? if so try this

control + alt + F7, when u press these keys simultaneously normal GUI desktop would be reached.

---

### Post by fknyeah on 2009-03-05
that didn't seem to do anything

---

### Post by abhilashm86 on 2009-03-05
oh ok, try this sometimes your GRUB loader seems to mess up by some boot splash images, so try following

1)at time of selecting boot options, press e to edit booting option- there may be unnecessary line or others attached,check those and delete them, then press enter and press b to boot.

2)either try recover method to login(other previous kernal).

keep trying various F1 -F12, because some systems change in the options, i had same problem after bootsplash images, i followed 1) method, worked fine.

---

### Post by fknyeah on 2009-03-05
i've never changed the splash screen though

---

### Post by avtolle on 2009-03-05
Did you upgrade to the 2.6.27.13 kernel recently, and not restart earlier? From the Grub menu, can you boot from an earler kernel? 

If you upgraded to a new kernel, and had (on an earlier kernel) manually installed the drivers for your graphics card, you will need to reinstall the drivers in the new kernel.

---

### Post by fknyeah on 2009-03-05
well, whatever I did, or whatever happened, it seems to be working now.  so strange.
Thanks for the help

SFK

---

### Post by abhilashm86 on 2009-03-05
> **fknyeah said:**
> well, whatever I did, or whatever happened, it seems to be working now.  so strange.
Thanks for the help

SFK

oh crazy:) yup i guess you rebooted your system, so everythings going fine :)

---

### Post by fknyeah on 2009-03-05
> **avtolle said:**
> Did you upgrade to the 2.6.27.13 kernel recently, and not restart earlier? From the Grub menu, can you boot from an earler kernel? 

If you upgraded to a new kernel, and had (on an earlier kernel) manually installed the drivers for your graphics card, you will need to reinstall the drivers in the new kernel.

So in being stressed out before, I didn't realize that this is what I did.  Except I don't know how to, or what to do about the drivers being reinstalled.  Could someone help with this?

---

### Post by fknyeah on 2009-03-06
bump

---

