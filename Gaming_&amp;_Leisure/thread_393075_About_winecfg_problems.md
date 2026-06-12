---
title: "About winecfg problems"
date: 2007-03-25
forum: Gaming &amp; Leisure
---

### Post by gtcoffee on 2007-03-25
hi all....
i think i have a problem with "winecfg"...

$ winecfg
wine: creating configuration directory '/home/gtcoffee/.wine'...

the upper msg will just stay there and never stop/finish...
and it would created a directory like ".wine-HcLjxb" , everytime it gave me different suffix for .wine-XXXXX......

---

### Post by cisforcojo on 2007-03-26
I had that exact same problem.

remove ALL the wine folders AND completely remove wine.
.wine
.wine-asldkfjdf (you get the point)

Reinstall it and then run:
$ wineprefixcreate
THEN
$ winecfg

If this doesn't work, post output of wineprefixcreate and winecfg.

---

