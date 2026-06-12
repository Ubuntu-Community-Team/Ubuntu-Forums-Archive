---
title: "Utility to dump portion of hard drive"
date: 2009-03-02
forum: General Help
---

### Post by hexanol on 2009-03-02
Hi,

I'm looking for a utility who can dump portions of the (raw) content of my hard drive. Right now, I'm using "hexdump" on my hard drive block device (/dev/sda), but it doesn't work well when it's time to look for informations far from the start of the disk (it takes a really long time). I though about using "dd" and then using "hexdump" on the file created by dd, but that's not the best option since you have to be extra careful when using dd (not to mistake the "if" and "of" parameters...).

I have look a bit on the web. No luck.

Anyone has suggestions ? Thanks!

---

### Post by CrucifiedEgo on 2009-03-02
dd isn't too complicated, as long as you remember what you're doing.  if=input file, of=output file.  you could use 'cat' as well on the block device... something like cat /dev/hda > ~/diskimage.img -- i've used this to create ISO images from CDs and it's worked fine, it should work just as well on a hard disk.

---

### Post by hexanol on 2009-03-02
Yeah, but even if it's simple to remember what "if" and "of" stands for, the last thing I want to do is make a mistake (even if I have backup, that would still be undesirable). Probability of such happenings are low, but not zero, and I would prefer they stay at zero. :)

---

### Post by HermanAB on 2009-03-02
Well, dd is best and most higher level disk debug programs use that at the bottom, so you can just as well get used to it.

Cheers,

Herman

---

