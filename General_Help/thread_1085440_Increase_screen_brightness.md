---
title: "Increase screen brightness"
date: 2009-03-03
forum: General Help
---

### Post by .gurkburk on 2009-03-03
Im running a laptop (m860u / kobalt nexus) and im trying to get the brightness up in ubuntu (got 8.10).
In bios and windows, I can just use the fn+F8 and F9 to adjust it, this doesnt work in linux however, and the screen brightness is really low and its annoying to work with it.

Ive tried a couple things, I have no settings for brightness in System/Settings/Power Management, ive also tried using something called "smartdimmer" but that just fails:
> smartdimmer -g
init_nvclock() failed!

And I tried to do the following from some forum about a similiar problem on a dell:
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness

But I found out that my /proc/acpi/video is an empty folder.

Any hints?

---

### Post by handy on 2009-03-03
I'm not sure, but you may be able to map the keys on your notebooks keyboard to do the job.

I don't personally use Ubuntu, so I can't investigate it any further, but if nothing else my post will bump your thread.

Good luck with it. :)

---

