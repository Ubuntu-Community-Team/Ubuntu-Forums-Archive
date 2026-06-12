---
title: "Sluggishness/Multicore"
date: 2008-04-06
forum: Desktop Environments
---

### Post by TerabyteUK on 2008-04-06
I've been running ubuntu 7.04 for the past year.
Having only needed to use it to run firefox, eclipse and a few other programs, I noticed a general sluggishness in the way it performs, dare I say even more slugging that similar operations in vista. (dual boot).

Something I now wonder, I have a dual core setup, does ubuntu (by default) take advantage of this? Could this be why? If it doesn't, is there anyway of getting it to do so? Is this planned for future versions etc etc....

I have not yet tried the latest version, perhaps there has been a speed up, since 7.04

Thanks for any info

---

### Post by sdennie on 2008-04-06
I believe that even in Ubuntu 7.04, the kernel knows about mult-core CPU's and utilizes them correctly.  You can verify this by doing a 'cat /proc/cpuinfo | grep "model name"'.  If it shows more than 1 CPU, you should be fine.

What specifically is sluggish?

---

### Post by trippinnik on 2008-04-07
How much memory do you have? How much hard disk space do you have free?  How many extensions do you have loaded in Firefox?  What version of the Flash player do you have? > What specifically is sluggish? 2nd that!

---

### Post by TerabyteUK on 2008-04-07
> **trippinnik said:**
> How much memory do you have? How much hard disk space do you have free?  How many extensions do you have loaded in Firefox?  What version of the Flash player do you have?  2nd that!

memory 3gb,
disk space ~ 200gb,
plugins, the same number as I have in windows. (Adblock, greasemonkey running autologinJ script).

Opening firefox is slow, click, watch the circle busy icon for a few seconds longer than I should, watch the window open, blank background, then fill with my homepage.

I mean it's bearable, and I feel as if i'm being fussy, but it IS slower than windows on what is a fairly fast setup, and I don't see why it should be. (Of all things, it shouldn't be slower than vista).
Perhaps this is just a firefox thing, now with the new version coming out, and 8.04 coming out too, perhaps things will be faster.

---

