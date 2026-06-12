---
title: "martian_modem issue: the kernel module seems to be deleting itself at random"
date: 2008-12-06
forum: General Help
---

### Post by AFarris01 on 2008-12-06
Ok, im trying to figure out this issue, and i don't know what's going on.  
I helped my friend get martian_modem installed on an old computer so he could use the modem in it, and replace the even older computer he had been using to get on the internet.

now heres the problem... i got the scanmodem tool, went through all the steps to find the driver, get/make/install martian_modem, and all, then finally added the martian_dev to the /etc/modules file, and everything worked fine.  however, every few days now, the kernel module appears to delete itself.

trying to launch the martian_modem helper program, rather than doing what it's supposed to, simply says that martian_dev isnt loaded, and when i try to do a "modprobe martian_dev" it says file not found.

why is this happening?  is there anything i can do to stop it?  right now, the only way i've found to fix it is to rebuild the whole thing from scratch, because trying to build the kernel modules alone generates errors.

his system is set up running hardy 8.04.1, and wvdial/gnomePPP used to connect to the internet

any ideas, anybody?

---

