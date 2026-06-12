---
title: "dell 1530 and media direct button"
date: 2008-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mattsnowboard on 2008-06-24
Ok, I'm about to install Ubuntu on my dell with media direct (3) crap.

Anyway, I have the Dell EISA partition, then Vista, then unallocated space, then the extended partition with the Dell media direct.

I want to know the best thing to do, can I install Ubuntu in the Extended partition that Media Direct is in? So I leave that intact and avoid the issues with "the button" killing my MBR. Or is there any way at all to get rid of Media Direct, and as long as that first Dell partition exists, the Media Direct button will safely boot into something (Ubuntu?) usefully and harmlessly?

I don't care much for Media Direct if I can avoid it, but I really want a stable system that won't get destroyed by an accidental press of the media direct button.

---

### Post by mattsnowboard on 2008-06-24
Sprry to bump but after using gParted on PartedMagic live cd to shift my vista partition back over the old recovery partition (I shrunk it in vista to be safe), and then recovering Vista (because it had changed in the partitions) following this [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

I uninstalled Media Direct in Vista (so there is still the separate partition) then booted with media direct and after some loading, it showed a white screen with an exit button.  I waited then hit exit and it showed the normal Media Direct then basically shut down.  I booted again with the button and it went to Vista.  Does this mean I can remove my stupid last (Media Direct) partition?

---

