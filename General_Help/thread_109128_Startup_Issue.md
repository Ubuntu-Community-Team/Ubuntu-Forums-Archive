---
title: "Startup Issue"
date: 2005-12-27
forum: General Help
---

### Post by Greeface on 2005-12-27
When I start Ubuntu it goes normal until it gets to 'loading modules.'  When it gets to that USplash closes and it says: ```
[4294720.363000]sda: assuming drive cache: write through
```

Then it continues to boot normally (without USplash, of course).  Next, when it gets to 'setting up LVM volume groups' it hangs for a while, and then says the same thing as above again.

I guess it's not that big of an issue, but It is kind of annoying since it takes a lot longer to start than normal.

Thanks for any advice,
~Greg

---

### Post by calt129 on 2005-12-29
[QUOTE=Greeface]When I start Ubuntu it goes normal until it gets to 'loading modules.'  When it gets to that USplash closes and it says: ```
[4294720.363000]sda: assuming drive cache: write through
```
[/QUOTE]


I'm also interested in an explanation, so far I've had no luck :(

OTOH, I think this may be more than just a small annoyance, because write-through mode has (empirically) much worse responsiveness than write-back mode...

---

### Post by FLeiXiuS on 2005-12-29
This looks like a debugging message for a USB storage device of some sort.  Whether it be an ipod, flashdrive, cellular device, or possibly an external hard drive.

---

### Post by calt129 on 2005-12-29
Not quite. I'm experiencing it with HDDs under VMware as well. A search on Google reveals many similar results, ppl are having this problem with their fixed disks, too.

---

### Post by Greeface on 2005-12-29
Well, I did just hook up a SD Card reader around when it started happening, so i will try unplugging it next time I boot.  Thanks for the tip, and I'll be trying this soon.

---

### Post by Greeface on 2005-12-30
Ah, FLeiXiuS, you're a genius!  Thats exactly what it was, I unplugged the card reader before I booted, and viola, it loads perfectly.

Thanks for the help

---

