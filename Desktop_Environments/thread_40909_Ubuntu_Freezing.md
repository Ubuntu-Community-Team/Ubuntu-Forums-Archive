---
title: "Ubuntu Freezing"
date: 2005-06-11
forum: Desktop Environments
---

### Post by Krogen on 2005-06-11
Hey everyone!

I decided to check out Ubuntu after failing to get everything working in multiple Linux distributions (Knoppix, Kanotix, Gentoo, Fedora Core 3). So I downloaded a standard 32 bit iso, burned it.

Succesfully installed on my old Kanotix partition.

Booted, logged in. Everything nice and sweet. Installed NVIDIA drivers. Rebooted. Selected Ubuntu from the grub menu, booted. Typed in my username and password, enter, LOCK-UP. Rebooted, force disk check. Rebooted again and after logging in, the same exact lock-up. Hard.

If it helps, I had a similar, if not exactly the same, problem in Kanotix (which I did get to work after multiple reinstallations... Somehow) and I also had the same problem in Fedora Core (freezing on logging in). 

Any ideas? I'm pretty sure this is a hardware problem with either my NVIDIA 6800 or VIA sound chip. 

Why the VIA sound chip? When I installed fedora core 3 it prompted me that the sound might create problems or might not work... Dunno.

Suggestions? I looked into my xorg file and everything there is generic. Last but not least, I do get the NVIDIA screen when booting.

Here's what's inside my box:
AMD Athlon 64 3200+
Albatron K8X800 Pro 2 motherboard 
NVIDIA 6800 by Gigabyte
120GB Seagate HD
1GB 3200 RAM
DLINK ethernet card, DLINK router

Thanks!

---

### Post by Krogen on 2005-06-11
...bump...  :-|

---

### Post by osorensen on 2005-06-11
Tried swapping some old hardware or tried disabling VIA chip to check whats causing it ?

can try an old grahics card or something, might help to locate whats causing it, then u can go from there  :smile:

---

### Post by Krogen on 2005-06-11
Hm... I reconfigured xorg (with "dpkg-reconfigure xserver-xorg"), set everything up, rebooted. Worked.

Then I rebooted again and it froze at the same spot while loading. What is up with this thing  ](*,) 

Thanks for the reply.

---

