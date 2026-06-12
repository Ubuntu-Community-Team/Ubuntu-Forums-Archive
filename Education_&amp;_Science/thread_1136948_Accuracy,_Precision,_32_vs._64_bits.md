---
title: "Accuracy, Precision, 32 vs. 64 bits ???"
date: 2009-04-25
forum: Education &amp; Science
---

### Post by Bean Street on 2009-04-25
Probably posted many times, but I didn't find much

We have just completed 24 hr runs of some elastic modeling, finite element, code on:

Intrepid Ibex, 32 bit, 2.6.27.11
CentOS 5.3, 64 bit  2.6.18.xxx

and are comparing the results.  This code is a blend of F77 and C, and depends solely on libc, etc.

What we find is that the two results differ on the order of 1%.
We can provide more details if needs be, but can also say that
despite Matlab's claims of bit-accurate cross-platform results,
that we have seen the same kinds of differences in Matlab on
32 vs 64.

So the simple spin on this shows three obvious axes of possibilities:

1) It's caused by the 32bit vs. 64bit kernel/libc differences.
2) It's caused by the differences between Ibex & CentOS (Very doubtful)
3) It's caused by the hardware differences (Both are DELL, Not sure AMD vs Intel, etc. But I am reaching for my flashlight to find out!)

So ...  rounding error?  FP stuff?,  Compiler flags?  Hmmmm....
Anyone having similar experiences, or know wassup?


Thanks ya'll...!

---

### Post by ssam on 2009-04-25
```
cat /proc/cpuinfo
```
to find the cpu details

If you put a number in a double, it will use 64bits on 32 or 64 bit platforms (for x86 and most compilers).

one cause of difference is that if calculations are done on with the x87 instructions, it get held in 80 bit precision. depending on compiler optimisations, it numbers may stay at 80bit for a few operation before being truncated back to 64 bit. this can cause variations. see [http://gcc.gnu.org/wiki/x87note](http://gcc.gnu.org/wiki/x87note) for more info.

the gcc man pages says that using sse (instead of 387) is default on x86-64 platforms. you should be able to force it on 32bit using something like
-mfpmath=sse -msse -msse2

---

### Post by neoflight on 2009-04-27
> **Bean Street said:**
> Probably posted many times, but I didn't find much

We have just completed 24 hr runs of some elastic modeling, finite element, code on:

Intrepid Ibex, 32 bit, 2.6.27.11
CentOS 5.3, 64 bit  2.6.18.xxx

and are comparing the results.  This code is a blend of F77 and C, and depends solely on libc, etc.

What we find is that the two results differ on the order of 1%.
We can provide more details if needs be, but can also say that
despite Matlab's claims of bit-accurate cross-platform results,
that we have seen the same kinds of differences in Matlab on
32 vs 64.

So the simple spin on this shows three obvious axes of possibilities:

1) It's caused by the 32bit vs. 64bit kernel/libc differences.
2) It's caused by the differences between Ibex & CentOS (Very doubtful)
3) It's caused by the hardware differences (Both are DELL, Not sure AMD vs Intel, etc. But I am reaching for my flashlight to find out!)

So ...  rounding error?  FP stuff?,  Compiler flags?  Hmmmm....
Anyone having similar experiences, or know wassup?


Thanks ya'll...!


Excellent. Could you please provide a detailed report. Is it possible for you to put one [here]("http://caejournal.com/index.php") (see my signature) as well? I am really interested in this study. /me work on FEM a lot. 

I have seen that matlab 32 and 64 difference. But do not have a supporting data now.I was too lazy to document that at that time. 

My guess is on the compiler stuff. 
Thinking aloud: 
1. algorithm used to solve the matrices? # of iterations? 
2. how about comparing say, just centOS 32 and centOS 64? 
3. error rate? iterations vs % error? see when it started to diverge ? 


I am very interested in pursuing this discussion further.

---

