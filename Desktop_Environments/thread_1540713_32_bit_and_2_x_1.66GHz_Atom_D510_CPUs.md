---
title: "32 bit and 2 x 1.66GHz Atom D510 CPUs"
date: 2010-07-28
forum: Desktop Environments
---

### Post by louis_mallow on 2010-07-28
I'm buying a new fanless desktop unit with 2 x 1.66GHz Intel Atom D510 CPUs. The vendor calls these a '64-bit processor'. But the unit has just 4Gb of memory and I don't want the fuss of 64-bit for the basic stuff I do. So I asked them to load Lucid-32.
 
Will the processors work with 32-bit?
 
Edit: The vendor tells me 32-bit won't make full use of the 4GB, only three and a half, but all else will be fine. So they'll load 32 and I'll try a live DVD of 64 in my own time. But I thought 32 bit was fine up to and including 4GB of memory?

---

### Post by 3Miro on 2010-07-28
> **louis_mallow said:**
> 
Edit: The vendor tells me 32-bit won't make full use of the 4GB, only three and a half, but all else will be fine. So they'll load 32 and I'll try a live DVD of 64 in my own time. But I thought 32 bit was fine up to and including 4GB of memory?

This is not true. There is the 32bit pae kernel that will take full advantage of 4GB RAM. I had a computer that was 64-bit (Athlon 64 X2) and I had 4GB of RAM, then I got a newer computer and gave my old one to my mom, however, she had a printer that she wanted to use and the printer only had 32-bit drivers. So I decided to install Lucid 32bit and ignore the RAM that will get wasted. However, the installation loaded the pae kernel by default and the system is now taking full advantage of all of the 4GB of RAM.

The only difference on 64 vs 32 is the speed. Regular 64 bit is the fastest, regular 32-bit is slower and pae is theoretically even slower. The difference, however, depends on the applications that you are running and on an Atom it may not be much anyway.

---

### Post by bouncingwilf on 2010-07-28
I recently built a small dedicated boat PC based on the D510 motherboard and installed UNR with just 1gb ram. There were  no installation errors and the whole system works very well and surprisingly fast. The app I'm running does its extensive math routine at 4 or 5 times the speed of a single atom based netbook running UNR and 1gb. -  Hope that helps.

---

