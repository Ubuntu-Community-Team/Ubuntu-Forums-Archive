---
title: "where my X-server goes?"
date: 2005-06-09
forum: Desktop Environments
---

### Post by irado on 2005-06-09
:???: 

hi, people..

I was trying to solve a resolution problem (another post) when decided to kill the XF86config-4 (sort of) configuration file, inorder to start with a completely empty file.

Unfortunately, due to a power sortage my pc rebooted and.. I am unable to access my Ubuntu, it simply enters in a completely blank (black) screen, with no further action. Is there a way to start Ubuntu in console mode, inorder to (re)configure my X-server?



TIA

---

### Post by Markrian on 2005-06-09
Can you be more specific? Does the grub menu appear, and the kernel boot? Do you see a list of started services? How far does it get before you see a blank screen?

If you get grub to come up, you can select the 'single' (single user) mode Ubuntu kernel, which only loads a minimal system to fix things in.

Alternatively, you could get the Ubuntu (or knoppix, or any other LiveCD) and boot from that, and manually edit the config files on the disk from there.

---

