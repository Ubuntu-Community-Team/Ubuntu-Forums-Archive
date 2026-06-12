---
title: "Restart Hangs Every Time"
date: 2007-08-17
forum: Dell  Ubuntu Support
---

### Post by CarlosinFL on 2007-08-17
When I tell my Dell Optiplex GX 745 to reboot, I get the Ubuntu splash screen showing the orange progress bar and when the orange is all gone, it hangs and never fully reboots automatically like it should. I have to press and hold the power button for 3 seconds to manually shutdown and power back on.

I don't know why or how to resolve this.

Any thoughts?

---

### Post by jacob01 on 2007-08-17
im not sure but can you go into a terminal by holding  ctrl+alt+f2 when the restart hangs

or maybe this be a kernal panic  or what ever its called im not sure

---

### Post by pparks1 on 2008-04-29
Well, this is an old question, but it does seem to arise from time to time.   I've experienced this problem on Dell GX745 workstations in Ubuntu and Fedora.  The resolution is the same in both cases.

You have to modify the kernel line in grub.   At the end of the line append on the following;

reboot=b

---

