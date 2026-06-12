---
title: "Upgrade Dell Dimension to 4Gb - is it worthwhile?"
date: 2009-01-06
forum: General Help
---

### Post by jarthurs on 2009-01-06
I have a Dell Dimension 5000 with a Pentium 4 (530) processor. I was originally intending to upgrade to 4Gb and install Ubuntu 64bit, but I've now found that the 530 implementation of the Pentium 4 doesn't support Intel 64bit architecture.

I am assuming this means I won't be able to address all of the 4Gb of memory, so should I just drop in three 1Gb DIMMs and re-use the existing 512Mb module to give me 3.5Gb, or are there any benefits in just going to the whole 4 x 1Gb DDR2 DIMMs?

Regards,
Jason.

---

### Post by HereInOz on 2009-01-06
In my opinion, no benefit, unless there is a cost benefit in using 2 x 2GB modules.  Unless you are involved in running multiple virtual machines, I have never seen Ubuntu use more than 1GB RAM anyway, but perhaps I am not a heavy RAM type of user.

I have installed 4GB on several machines with 32 bit systems, but simply because the cost was lower with 2 x 2GB.

---

### Post by sdennie on 2009-01-06
You should still be able to use all 4GB of RAM with a 32-bit OS.  See the second section of this guide: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by hangfire on 2009-01-06
> **jarthurs said:**
> I have a Dell Dimension 5000 with a Pentium 4 (530) processor. I was originally intending to upgrade to 4Gb and install Ubuntu 64bit, but I've now found that the 530 implementation of the Pentium 4 doesn't support Intel 64bit architecture.

The 530 does support the emt64 instruction set, and I have run 6.06LTS 64bit on it, on a little Dell Dimension with 4GB of RAM.

[http://www.intel.com/design/Pentium4/datashts/302351.htm](http://www.intel.com/design/Pentium4/datashts/302351.htm)

It was worth it (for me) because it was a mini-server running both Oracle EE (not supported) and MySQL + Wiki. I doubt a regular user would use more than 2GB though, and 1GB is usually enough. It's not Vista, after all.

-HF

---

