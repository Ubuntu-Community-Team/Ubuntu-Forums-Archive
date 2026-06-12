---
title: "[B]Dual Boot Problem[/B]"
date: 2009-01-19
forum: General Help
---

### Post by dublinfireman on 2009-01-19
I'm having a problem with my dual boot.  I have set ubuntu as primary and windows as slave, added 

title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

and when I try to boot to windows, it says starting up and freezes.

I can boot to windows fine if I unhook the ubuntu drive.

Any ideas???

---

