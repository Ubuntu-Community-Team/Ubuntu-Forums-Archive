---
title: "686 optimized packages/distribution"
date: 2006-07-05
forum: Desktop Environments
---

### Post by kpkeerthi on 2006-07-05
Just curious... Why is that all 32-bit linux distributions are compiled for 386 architecture by default? Why isn't there a distribution that has *all* packages compiled for the modern 686 architectures? 
Having used the 686-optimized Swiftfox, I'm quite impressed with it. Wouldn't it be nice to have an (ubuntu) distribution built solely for the 686s?

---

### Post by Nathaniel on 2006-07-05
Try ZenWalk :)

---

### Post by atoponce on 2006-07-05
[quote=kpkeerthi]Just curious... Why is that all 32-bit linux distributions are compiled for 386 architecture by default? Why isn't there a distribution that has *all* packages compiled for the modern 686 architectures? 
Having used the 686-optimized Swiftfox, I'm quite impressed with it. Wouldn't it be nice to have an (ubuntu) distribution built solely for the 686s?[/quote] I too find this very annoying.  Find anyone that is still on a 386, 486 or even 586 for that matter.  While I am not supporting  building for 686 only, 386 is a dead architecture, and should be removed from future releases.  If anything, when downloading an *.iso, the user should have a choice with architeture and it should default to 686.  I see no reason to supprt 386 or 486.  Alienating the < .0001% of market that uses those two architectures for the benefit of the community shouldn't matter.

---

### Post by mannheim on 2006-07-05
Although the packages have "i386" in their name, they are not compiled for 386, and 386 processors are not supported. They are compiled using the i486 instruction set and optimized for Pentium 4 processors. This is from the Ubuntu support FAQ:

>         Ubuntu packages for the i386 architecture are compiled using the i486 instruction set (-march=i486), with instruction choices based on the Pentium 4 processor (-mcpu=pentium4). This combination provides benefits for modern processors without sacrificing compatibility with older and embedded devices.


Some software (such as codecs) contain code using MMX or SSE instuctions or whatever, and that code is used if the CPU supports it.

---

### Post by atoponce on 2006-07-05
I am not just talking about packages, but more specifically, the kernel.  When upgrading from the 386 kernel to the 686 kernel, there was a noticable speed increase when using CAS software, querying large databases, compiling software and even playing games.

But even using the 486 instruction set to compile packages seems silly to me, seeing as though it is a dead architecture.  If the packages are optimized for the Pentium 4 series processors, then they need to be compiled using the 686 instruction set.

Am I off base here?  Am I missing something?

---

### Post by 23meg on 2006-07-05
This has been discussed before:

[http://ubuntuforums.org/showthread.php?t=26706](http://ubuntuforums.org/showthread.php?t=26706)
[http://ubuntuforums.org/showthread.php?t=199343](http://ubuntuforums.org/showthread.php?t=199343)
[http://ubuntuforums.org/showthread.php?t=172962](http://ubuntuforums.org/showthread.php?t=172962)
[http://ubuntuforums.org/showthread.php?t=169422](http://ubuntuforums.org/showthread.php?t=169422)

Thus this thread is redundant.

[QUOTE=atoponce]Am I off base here? Am I missing something?[/QUOTE]Possibly. Take a look at the discussion and facts in the threads above.

[QUOTE=kpkeerthi]Why isn't there a distribution that has *all* packages compiled for the modern 686 architectures? [/QUOTE]There's more than one. Check out Arch Linux for an example.

---

