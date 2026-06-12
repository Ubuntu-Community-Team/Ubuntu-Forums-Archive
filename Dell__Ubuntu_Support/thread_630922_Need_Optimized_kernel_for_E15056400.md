---
title: "Need Optimized kernel for E1505/6400"
date: 2007-12-03
forum: Dell  Ubuntu Support
---

### Post by lifeontilt on 2007-12-03
Hi, I just installed Gutsy on a Dell Inspiron 6400 laptop which has an Intel Core2 Duo processor
I know that aside from the Generic linux kernel, I can optionally use the real time kernel that come pre-installed with Ubuntu Studio. My question is.... what are my options (if any other) for a possibly more optimized kernel as far as Intel Core2 duo processors are concerned. I am willing to compile my own as a last resort if need be.

Also do the dell installed laptops come with a generic kernel or somthing a bit more optimized.:KS

BTW does dell provide people with restore cds in case something goes wrong? and if yes is this cd still open source and if yes where can i download it. I know its a lot of questions but please answer the best you can about what you can. I Appreciate any help. :)

---

### Post by m94mni on 2007-12-04
There is no reason to try to optimize the kernel on x86 - the kernel does runtime optimization anyway these days. That's why the -i686 kernel was discontinued some time ago.

---

### Post by neilius on 2007-12-04
The only thing you could do to squeeze a bit more out would be to use the x86-64 distribution of Gutsy. It runs well enough on my Celeron M based 6400 and would improve performance in situations where intense number crunching is needed - video encoding etc.

Rgds,

Neil.

---

### Post by m94mni on 2007-12-05
Agreed, 64bit would help for a few specific apps.

You should make sure you have libc6-i686 installed, as that contains a few 686-specific optimizations.

---

