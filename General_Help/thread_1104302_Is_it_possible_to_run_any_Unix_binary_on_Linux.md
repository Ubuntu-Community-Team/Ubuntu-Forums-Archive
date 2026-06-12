---
title: "Is it possible to run *any* Unix binary on Linux?"
date: 2009-03-23
forum: General Help
---

### Post by Repgahroll on 2009-03-23
I want to buy some very old programs that i am interested to run just to see how it works, pure curiosity.

But the programs are very old Unix apps, which i would buy from the internet on floppy.

And i want to know if it's possible to run under Linux.

Thanks.

---

### Post by aeiah on 2009-03-23
perhaps. if you could get the source, then you'd be fine. it depends how complicated the software is. if its pretty rudimentary you might not have a problem but you have to remember that unix and linux are different operating systems. hell, the software will probably not even run on all versions of unix nevermind linux.

---

### Post by lisati on 2009-03-23
I'd second the idea that it might be easier using the source - who knows what processor the old binaries were compiled for?

---

### Post by kpatz on 2009-03-23
They *might* work if they were compiled for x86.  No guarantees though, especially when it comes to system/kernel calls or library dependencies...

You'll have a better chance if source code is available.

---

### Post by Repgahroll on 2009-03-23
:( Isn't possible?

The programs are distributed as binary only. What's the bigger problem? (processor arch, kernel, etc)

No source code - Proprietary software :(.

EDIT:
Yes, they're compiled for x86 32-bit :D

Thanks

---

### Post by jespdj on 2009-03-23
Well, Linux is not Unix. For which kind of Unix were those old programs written? Different Unix-like operating systems are in general not binary compatible. Each operating system has its own system calls, and although there are some standards like [POSIX]("http://en.wikipedia.org/wiki/POSIX"), there are also many OS-specific system calls.

---

### Post by HavocXphere on 2009-03-23
Unlikely imo. The systems are compatible in broad terms...but thats like saying Mercs and BMW are both cars so their parts should be interchangeable.

If its only out of curiosity & the price is significant, then I'd say drop the idea.

Also, have you considered asking the company that produced this proprietary code? ;)

---

### Post by Repgahroll on 2009-03-23
Are old programs for engineering made by a not-known enterprise of my country. :)

There are DOS and Unix versions, but the Unix version is more powerful. The program was probably compiled for(/on) a 386 processor (maybe 486).

EDIT:
The company has bankrupted, has something like 20 years :)

Thanks.

---

