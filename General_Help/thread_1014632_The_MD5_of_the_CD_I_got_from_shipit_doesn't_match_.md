---
title: "The MD5 of the CD I got from shipit doesn't match the official MD5"
date: 2008-12-18
forum: General Help
---

### Post by tiesuoqiao on 2008-12-18
I ordered a free Ubuntu 8.10 LiveCD from shipit.ubuntu.com and one month later I received a Ubuntu packet sent from Netherlands.

Everything works very well. However, when I wrote the CD to ISO, and compared it with the one I downloaded from Ubuntu's web site, they do not match.

The one from Netherlands is larger in size
and the MD5 is 89434834DB92928CED2E703691B931BE

Is this Netherlands packet from Ubuntu?

---

### Post by Polygon on 2008-12-18
try the 'check cd' option or whatever in the live cd boot menu, if that checks out and it reports no errors, then the cd is fine, and its just made from a different file then the official iso from ubuntu.com

---

### Post by plucky on 2008-12-18
> and its just made from a different file then the official iso from ubuntu.com 


I don't think so.Where would they get this iso?


> try the 'check cd' option or whatever in the live cd boot menu, if that checks out and it reports no errors, then the cd is fine,

+1

You cannot use the MD5sum read from a burnt CD as sometimes when the CD is burnt,pad blocks are inserted during the burn.Do a google search for "md5sum" and "CD" for a better explanation of why this doesn't work.


Good Luck

---

### Post by eye208 on 2008-12-18
You can use "cmp" to compare two binary files. Insert the CD, then run
```
cmp /dev/cdrom imagefile.iso
```

If cmp reports no differences except for an EOF on the image file, then the CD is authentic.

---

