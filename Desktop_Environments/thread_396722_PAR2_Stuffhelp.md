---
title: "PAR2 Stuff/help"
date: 2007-03-29
forum: Desktop Environments
---

### Post by Ominide on 2007-03-29
Is there a par program that will combine a group of files like:
****.avi.001
****.avi.002
****.avi.003

Quick par does this, but gpar and pypar do not.
Any help would be great thanks.

---

### Post by teknosexual on 2007-06-01
I might be misunderstanding the question, but those extensions look like split RAR archives to me, which would need to be combined/extracted with RAR/UnRAR.

---

### Post by leguman on 2007-08-01
I'm a bit late

there are several ways to do it, have a look at this tutorial : [usenet binaries with linux]("http://linux-is-sexy.blogspot.com/2005/12/usenet-binaries-with-linux-tutorial.html")

quick answer : use the split files as additional blocks like this :

par2repair yourfile.par2 yourfile.avi.*

---

### Post by mptpro on 2008-07-12
thanks, that worked!

Anyone know of gui way of doingn this?

---

