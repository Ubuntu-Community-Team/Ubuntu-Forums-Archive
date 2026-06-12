---
title: "Quick /proc/meminfo units question"
date: 2009-05-20
forum: General Help
---

### Post by gldearman on 2009-05-20
Hi all,

/proc/meminfo lists memory in units of "kB."

Does anyone happen to know if that really means kilobytes, or if that actually means kibibytes?

I know, kibibytes should be "kiB," but a lot of older applications just used "kB," and rounded.

Thanks!

---

### Post by adrianx on 2009-05-20
I'm sure that it must be kiB, here's why:

free, references /proc/meminfo, If I *cat /proc/meminfo* it gives me:
MemTotal: [COLOR=Navy]       [/COLOR][COLOR=Navy]2797796[/COLOR] kB

Now, if I run *free -b*, I get 2864943104 bytes total.

2864943104 / 1024 = [COLOR=Navy]2797796[/COLOR]

That is the same amount that is reported by /proc/meminfo

---

### Post by gldearman on 2009-05-20
Thank you!

---

