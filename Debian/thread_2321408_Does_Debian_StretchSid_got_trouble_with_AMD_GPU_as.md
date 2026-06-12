---
title: "Does Debian Stretch/Sid got trouble with AMD GPU as Ubuntu 16.04?"
date: 2016-04-22
forum: Debian
---

### Post by 6975 on 2016-04-22
I was wondering long ago since Debian themselves only have xorg 
& firmware-linux-nonfree from the begining. 
[https://wiki.debian.org/ATIProprietary](https://wiki.debian.org/ATIProprietary)
Even install fglrx or Crimson from amd website will not work.

& Ubuntu 16.04 is based from Stretch/Sid.
or that's only affect on Ubuntu 16.04 based?

---

### Post by T.J. on 2016-04-22
The reason that you have FGLRX troubles is because AMD has depreciated the FGLRX driver.  They have not updated it for X.org 1.18.  As far as I know, they have no plans to, and want users to upgrade to the AMDGPU driver.  

Unless your video card has a GCN chipset - that is made in the last 4-5 years, the AMDGPU driver will not work.  If you have an older card, you will be forced to use the FOSS radeon driver in place of FGLRX for as long as you use Xorg 1.18 or newer.

I'd find out if you have a GCN card.  If you do, I'd switch to the AMDGPU driver if needed.

> I was wondering long ago since Debian themselves only have xorg & firmware-linux-nonfree from the begining.  

Debian has support for FGLRX, but only in Debian Stable at the present time.  The reason for this is that Debian Stable uses an older version of Xorg.  Since Debian Sid uses Xorg 1.18, the FGLRX driver doesn't work for them.  As a consequence, Ubuntu 16.04 - which is based on Debian Sid doesn't have FGLRX support either.

You could blame AMD for not giving us a smoother transition, but Canonical knew the problem existed and could have used Xorg 1.17 for 16.04 LTS instead, giving us more time at no loss of significant functionality.  But they didn't, so here we are.  If it is any consolation, I have always found the FGLRX driver to be intolerably buggy and never use it anyway. 

 If you are a gamer with a non-GCN card, looking for OpenGL 4 support, there is an experimental Mesa patch you can try that might get games working without the FGLRX driver.  (Naturally, your card must have hardware support for OpenGL 4 in order to try.) I have never tried it, so I cannot speak to it. If you are serious about gaming on Linux for the long-term, I would rather offer the advice of getting an Nvidia card instead.  Frankly, while AMD has been very helpful to the community and deserves a lot of praise for their efforts - awesome code, their video drivers still are far less than Nvidia's on Linux.

---

### Post by 6975 on 2016-04-23
Thank you for valuable information. 
Now my curious about fglrx between Debian & Ubuntu become fully cleared.

---

