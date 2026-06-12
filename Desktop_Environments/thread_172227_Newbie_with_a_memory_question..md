---
title: "Newbie with a memory question."
date: 2006-05-08
forum: Desktop Environments
---

### Post by PaLoBo on 2006-05-08
Hi all.

I started using linux about 6 months ago and ubuntu more specificaly about 1 month ago. Let me first say that Ubuntu has defenitly own another strong advocate.!

Now onto my question...

I have 512Mb ram on my system and have noticed that more than half of it is used for cache. Is this normal. I have few apps open and seem to have no memory available since cache is using so much. Could this cache be cleaned, or does it serve some purpose.

Thanks for any and all enlightenment.

---

### Post by mips on 2006-05-08
Post the output of **free**

I have 1GB and using about 320MB cache

---

### Post by Sef on 2006-05-08
Linux tends to take all the memory available and give it out to what ever application needs it.

For a detailed explanation, read this blog:

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html]("http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html")

---

### Post by GeneralZod on 2006-05-08
The cache is there so that frequently accessed files can be read straight from RAM, rather than the hard-disk (many, many times faster!).  When an application needs more RAM, the corresponding amount of cache will be instantly freed.

In other words, this is both normal, and healthy ;)

---

### Post by PaLoBo on 2006-05-08
Hi all,

Thanks for the input. As requested below is the output of free:

```

pedro@Lobo:~$ free
             total       used       free     shared    buffers     cached
Mem:        515988     507648       8340          0       7732     362412
-/+ buffers/cache:     137504     378484
Swap:      1510068     123992    1386076

```

As for this being normal and healthy, it makes sense, but why then is my PC sluggish. I'm sure it's just something I'm doing wrong. I will continue to scour the forum in search of an answer. I know many poeple are complaining about gnome being sluggish in general.

Once again, thanks for all and any help
cheers,
P.

---

### Post by Omnios on 2006-05-08
The cach thing kind of bothered me at first but found out that the Linux apps show cached ram where as the XP do not show all the cach as foudn out by using memory recovery programs. Linux does use a bit more ram but not as much as it seems with what is shown comparted to xp

---

