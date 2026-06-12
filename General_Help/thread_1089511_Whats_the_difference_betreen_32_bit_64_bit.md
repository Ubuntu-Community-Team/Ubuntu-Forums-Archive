---
title: "Whats the difference betreen 32 bit 64 bit"
date: 2009-03-07
forum: General Help
---

### Post by smooch101 on 2009-03-07
whats the difference of 32 bit and 64 bit,

i know 64 bit is AMD pcs and 32 bit is INTEL
but whats the real difference does it make the computer faster? or is that the requirement of a pc

---

### Post by martrn on 2009-03-07
> **smooch101 said:**
> whats the difference of 32 bit and 64 bit, i know 64 bit is AMD pcs and 32 bit is INTEL but whats the real difference does it make the computer faster? or is that the requirement of a pc

The difference is 32 bits.  [  (64-32=32) bits.  ]

If you have a 64bit cpu (AMD or Intel) based on the 64bit architecture (first specified by AMD), then you will be wasteing 32bit every cpu cycle.  Sometimes you don't need the extra 32 bit, sometimes you do. If your cpu every runs at 100% using 64 bits will make it faster.

---

### Post by Skripka on 2009-03-07
The main difference is how much memory you can address.

If you run 32bit, the most memory you can address is 2^32 ....which ends up being about 3.2 GB.  If you want to use more memory you either need to use hacks, or just run a 64bit distro.

---

### Post by miegiel on 2009-03-07
> **Skripka said:**
> The main difference is how much memory you can address.

If you run 32bit, the most memory you can address is 2^32 ....which ends up being about 3.2 GB.  If you want to use more memory you either need to use hacks, or just run a 64bit distro.

I noticed I also use about twice as much memory in 64bit compared to 32bit. It doesn't matter in my case (I have 2gigs),, but I think it went up from 600 meg to a bit over 1 gig.

---

### Post by hexanol on 2009-03-07
32 bit and 64 bit, when talking about OS, refers to the different instruction set architecture they target (x86 vs x86-64). Now, since x86-64 is an extension of x86, it is not a really different ISA but just a superset.

Basically, if you are not really computer literate, the difference is mostly about the total memory you can use and the fact that that some software will run faster on the new architecture. You can read a bit more about x86-64 on [wikipedia]("http://en.wikipedia.org/wiki/X86-64").

And that's normal memory usage goes up a little bit (but twice is a bit suspicious) since all programs hold a certain amount of "memory adress" and that it takes more space to store them when in x86-64.

---

### Post by smooch101 on 2009-03-07
Thanks

---

