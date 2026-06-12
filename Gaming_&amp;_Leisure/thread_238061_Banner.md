---
title: "Banner"
date: 2006-08-17
forum: Gaming &amp; Leisure
---

### Post by string on 2006-08-17
Not really gaming, but fun... so I thought here would be best ...

The banner command on Linux prints the _bi_ text vertically, is there anything similar that does it horizontally ? I think NetBSD's benner does it by default... by can't seem to find sources ...

I think I heard of another command doing like banner but horizontally and with a different "font" .... anyone knows ?

Thanks ^^

---

### Post by den benne on 2006-08-17
this is a cool command :D
I'ld also like to know if there's a command for a horizontal line

---

### Post by DoktorSeven on 2006-08-17
sysvbanner (in Universe) "prints out the first 10 characters of text in large letters", and does it horizontally.  Smaller letters though, and no font selection.

It does kind of override the other banner command (from bsdmainutils) since sysvbanner is put in /usr/bin with the command name **banner** and bsdmainutils's **banner** is in /usr/games; you can still run the vertical one with /usr/games/banner... ;)

---

