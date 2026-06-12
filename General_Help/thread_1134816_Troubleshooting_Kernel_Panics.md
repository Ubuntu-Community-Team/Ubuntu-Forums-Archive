---
title: "Troubleshooting Kernel Panics?"
date: 2009-04-24
forum: General Help
---

### Post by awyeah on 2009-04-24
I've been searching and searching, and I can't seem to find any way to be able to troubleshoot the kernel panics I'm having in 9.04.

It simply won't create a dump file in /var/crash.  All that happens as that X locks up and the caps lock and scroll lock lights flash.

Anyone have any advice on getting this to work?  I'd like to get a dump to analyze.

Thanks!

---

### Post by nandemonai on 2009-04-24
I'm far from an expert at this sort of thing, but is there anything of interest in /var/log/kern.log for the times of the panics?

I'm hazarding a guess that it's graphics related.

---

### Post by awyeah on 2009-04-24
Nope, nothing in there.  It could be anything.  This is a Dell Laptop, btw.  Inspiron 1520... Running 64-bit 9.04.

The other problem is, it doesn't seem to be tied to any particular action of mine - it seems random.  That's why I'm looking for basic info on at least getting it to dump to disk - that would be a good start...

---

