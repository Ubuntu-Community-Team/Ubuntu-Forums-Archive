---
title: "Graphics cards: known issues in 6.10"
date: 2007-02-04
forum: Desktop Environments
---

### Post by InsomniakF on 2007-02-04
Hi,
New here and I've been having problems with my screen res with onboard graphics Intel 89245G Express Chipset.
Screen res options were 800x600 highest. :(

Thinking of getting myself this card:
Sapphire Radeon X1600PRO 256MBDDR2 Pci-Express, Ultimate Edition.

Are there any known issues with this card and Ubuntu?
I'm running Edgy 6.10

Or... any recommendations for very compatible cards would be appreciated. :)

Thank you muchly!

---

### Post by mgmiller on 2007-02-04
I have Ubuntu 6.10 running on 2 machines one with Nvidia GF 6800  and the other ATI 9600.  I can tell you that you will have an easier time with Nvidia cards if you're a noobie.  I have my ATI card working with 3d acceleration and powering a TV display through s-video, but it was a real configuration problem to get everything working right.  I don't want to start a flame war re ATI vs. Nvidia, but IMHO, Nvidia seems to have better Linux support and is easier to configure.

---

### Post by dcstar on 2007-02-04
> **InsomniakF said:**
> Hi,
New here and I've been having problems with my screen res with onboard graphics Intel 89245G Express Chipset.
Screen res options were 800x600 highest. :(

Thinking of getting myself this card:
Sapphire Radeon X1600PRO 256MBDDR2 Pci-Express, Ultimate Edition.

Are there any known issues with this card and Ubuntu?
I'm running Edgy 6.10

Or... any recommendations for very compatible cards would be appreciated. :)

Thank you muchly!

In 6.10 I lost the hardware acceleration on my inbuilt S3 Unichrome hardware (which still works fine in 6.06), after much mucking around trying to get it going I purchased an old Nvidia AGP card for a few dollars and it works fine in 6.10 (actually it flies, better than my inbuilt stuff.........)   :)

---

### Post by InsomniakF on 2007-02-05
Thanks guys, got it sorted just now.

sudo dpkg-reconfigure xserver-xorg

That's what finally worked for me. :)

---

