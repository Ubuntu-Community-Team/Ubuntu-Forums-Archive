---
title: "Swap in/out s2tc lib for L4D2 / NWN"
date: 2015-07-10
forum: Gaming &amp; Leisure
---

### Post by nick.johnson on 2015-07-10
Hello,

After some years of combining various bits of parts of machines to keep something running, I decided to buy a new machine, a Pentium K G3258 with Intel HD graphics.

Whilst I'm not looking for top-end gaming, I find that I can play Left 4 Dead 2 reasonably well if I install libtxc-dxtn-s2tc:i386 on my amd64 install of Ubuntu 15.04

However, this stops my NWN install running at all, the process appears to hang with no output etc. I know that the install is good as I copied it from a disk on the working machine. I've done all the usual steps and installed the 32 bit libs. From a post I found on an ARCH forum, if I remove libtxc-dxtn-s2tc:i386 via apt, it works without issue, but my textures are missing in L4D2 (and I suspect any newer 3D FPS games should I get round to installing).

Is there a clean way to disable the offending lib from the command line (so I can throw it in a script) other than having to install/remove the library when I change game?

I've tried various commands from google such as force_s3tc_enable=false but to no avail. It seems that the texture compression is needed for the FPS games but something about the library causes issues with NWN.

Thanks,
-Nick.

---

### Post by MikeCyber on 2015-07-11
> **nick.johnson said:**
> Hello,

  I decided to buy a new machine, a Pentium K G3258 with Intel HD graphics.

-Nick.

Heja, that looks way outdated for a new PC. My 2year old has:
Intel® Core™ i7-4770K CPU @ 3.50GHz × 8 
GeForce GTX 770/PCIe/SSE2
16GB Ram

---

