---
title: "/dev/fd/*"
date: 2009-01-17
forum: General Help
---

### Post by ooobooontooo on 2009-01-17
Hi,

I was looking through the files in /dev/fd/ (using ls), and I found 5 more files than I expected. 0, 1, and 2 are stdin, stdout, and stderr like they should be. However, there is also a /dev/fd/3 which seems to be a link to some specific procedure (it links to some /proc/*/fd). I'm guessing this is the fd used by the ls command or something. Also, whenever I use tab-complete, I also get /dev/fd/6[0-3] and they link to some pipe:[*]. Can I anybody give me some insight as to what these are used for? I'd appreciate any links to readings as well. Thanks in advance.

---

### Post by albinootje on 2009-01-17
> **ooobooontooo said:**
> Hi,

I was looking through the files in /dev/fd/ (using ls), and I found 5 more files than I expected. 0, 1, and 2 are stdin, stdout, and stderr like they should be.

Hmmm, interesting.
This is perhaps not what you're looking for : [http://www.vias.org/linux-knowhow/bbg_sect_08_02_04.html](http://www.vias.org/linux-knowhow/bbg_sect_08_02_04.html)

But, meanwhile, I noticed a difference between :
```

ls -la /dev/fd/

```
and :
```

sudo ls -la /dev/fd/

```
As normal use I see 6 "pipes" there, as root there's none.

---

### Post by ooobooontooo on 2009-01-19
Yeah I looked at the link you gave me. It was an interesting read...sort of related, but I don't think it helped me in answering my question...unless I missed something. Anyway thanks. Does anyone else have a solution?

EDIT: Oh yeah, I tried what you were talking about with the sudo. Yeah, it didn't show any pipes when I tried with sudo.

---

