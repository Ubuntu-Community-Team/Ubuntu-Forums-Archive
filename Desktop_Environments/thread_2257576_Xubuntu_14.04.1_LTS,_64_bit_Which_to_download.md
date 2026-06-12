---
title: "Xubuntu 14.04.1 LTS, 64 bit: Which to download?"
date: 2014-12-20
forum: Desktop Environments
---

### Post by Kurt_Alan on 2014-12-20
The xubuntu download site offers two possibilities:

a. PC (Intel x86)
b. 64-bit PC (AMD64)

Which to download? Now, when I look at this, I think that a. is for Intel processors and that b. is for AMD processors.

I have Intel, 64 bit.

a. doesn't say if it's 64 bit, so I think I should opt for b. But b. says that I have an AMD processor, which I don't.

Which to download for Intel, 64 bit?

---

### Post by Dennis N on 2014-12-20
For Intel 64 bit processors, you can use either. But to take full advantage of the 64 bit CPU registers, you would use (b).

Edit: Also, to be sure you can use the most of the memory you have (16GB) you should use (b)!

---

### Post by Impavidus on 2014-12-21
It doesn't mean one is for Intel processors and the other for AMD processors. This 32 bit instruction set was introduced by Intel, so it's know as the Intel 32 bit instruction set. This 64 bit instruction set was introduced by AMD, so it's knows as the AMD64 instruction set. Intel had introduced its own 64 bit CPU before, using a different instruction set, but the AMD64 was compatible with 32 bit software. Nowadays both Intel and AMD CPUs use the same AMD64 instruction set.

---

### Post by Kurt_Alan on 2014-12-21
> **Impavidus said:**
> It doesn't mean one is for Intel processors and the other for AMD processors. This 32 bit instruction set was introduced by Intel, so it's know as the Intel 32 bit instruction set. This 64 bit instruction set was introduced by AMD, so it's knows as the AMD64 instruction set. Intel had introduced its own 64 bit CPU before, using a different instruction set, but the AMD64 was compatible with 32 bit software. Nowadays both Intel and AMD CPUs use the same AMD64 instruction set.

Thanks for this clarification.  It seems that you are saying that the AMD64 64 bit instruction set is backward compatible to 32 bit, so one could not go wrong making this selection. Correct? If so, why doesn't the xubuntu site (or anybody else) just use the AMD instruction set? Any why does the xubuntu site not state whether the Intel OS selection is 32 or 64 bit. Or are they both 64 bit backward compatible to 32 bit?  Maybe it is confusing or maybe I'm still confused, but now I know that we are talking about instruction sets and not processors per se.

---

### Post by Dennis N on 2014-12-22
> why doesn't the xubuntu site (or anybody else) just use the AMD instruction set?

If you mean why don't they only offer 64 bit versions of the OS, it's because there are plenty of 32 bit Intel CPUs still around, and they can't process 64 bit length instructions. So we need the 32 bit OS version as well.

---

### Post by Kurt_Alan on 2014-12-22
Got it. 64 bit (AMD instruction set) is backward compatible to 32 bit processors but it is not 32 bit. The Intel 32 bit instruction set is for people who have 32 bit processors--even though Intel did (does?) also have a 64 bit set (according to Impavidus).

---

### Post by mörgæs on 2014-12-22
> **Kurt_Alan said:**
> Got it. 64 bit (AMD instruction set) is backward compatible to 32 bit processors but it is not 32 bit.

No. A 64 bit operative system runs only on 64 bit processors but a 32 bit runs on both. Forget about the Intel / AMD distinction.

---

### Post by Impavidus on 2014-12-22
Once there was just 32 bit (and 16 bit before that, and some exotic systems used 18 bit or whatever). Then Intel came with the Intel 64 bit instruction set, used by the Intel 64 bit processor. However, the Intel 64 bit processor could not run 32 bit software and as most proprietary software was only released in 32 bits this software couldn't run on the Intel 64 bit processor. Nobody wanted the processor because there was no software to run on it and nobody made the software because nobody owned the processor. That processor never caught on.

Then AMD introduced their own 64 bit instruction set, to be used by their 64 bit processor. This processor could run all existing 32 bit software. People were willing to buy this processor to be future-proof and once enough people had AMD64 CPUs it became interesting to sell 64 bit software, solving the chicken-and-egg problem. Then AMD and Intel made some deal, a kind of patent exchange, and Intel received the right to produce processors using the AMD64 instruction set. So nowadays we no longer have to care whether it's AMD or Intel, they both run the same binary code.

---

### Post by raptir on 2014-12-22
> **Kurt_Alan said:**
> Got it. 64 bit (AMD instruction set) is backward compatible to 32 bit processors but it is not 32 bit. The Intel 32 bit instruction set is for people who have 32 bit processors--even though Intel did (does?) also have a 64 bit set (according to Impavidus).

No, what was meant by the AMD64 instruction set being backwards compatible is that AMD64 processors can still run 32-bit software, **not** that 64-bit software can run on a 32-bit processor. Intel had developed "IA-64" which is not used in any consumer PCs and was not compatible with 32-bit software. Essentially, ignore the AMD vs Intel part. The 32-bit architecture is often called x86 while the 64-bit architecture is often called x86-64. 

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

The Xubuntu download page calls it "64-bit PC" or "32-bit PC", which is the easiest way to think of it. If you have a 64-bit processor you should probably install the 64-bit version. There are very few reasons to install a 32-bit OS on a 64-bit processor.

---

### Post by Kurt_Alan on 2014-12-22
Marked "SOLVED" by OP.

---

