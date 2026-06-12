---
title: "Grub loading missing last character"
date: 2010-10-22
forum: Desktop Environments
---

### Post by newDrapersDrakeUser on 2010-10-22
Hi

I am currently running ubuntu 10.10 Gnome version on my desktop.
My machine is having a dual boot with Windows 7. I am facing one strange problem at the time of booting the OS. Whenever i try to boot any OS using my grub2 (1.98 experimental version) it comes back with file not found error.

i tried getting into the command line on GRUB to understand the root of the problem, and found that the last character in the GRUB is missing for all the entries (i.e instead of "generic" only "generi" missing "c" in the end). The grub.cfg file has all the entries as expected.

I tried running sudo upgade-grub couple of time but problem still remains.

I also did a reinstall of grub2,grub-pc,gfxboot packages using the synaptic but did not get any benifit out of it.


The Workaround for me is to manually edit grub.cfg after every update-grub command and add one extra character in the end.

Can you please suggest if there is a way to get this corrected.

Thanks in advance

---

### Post by newDrapersDrakeUser on 2010-10-29
I installed BURG yesterday and now i don't need to edit the burg.cfg file.

Thanks

---

