---
title: "DWM Problem patching with Transparency"
date: 2012-01-11
forum: Desktop Environments
---

### Post by kanazky on 2012-01-11
Config: [http://pastebin.com/DmQSFJ8D](http://pastebin.com/DmQSFJ8D)


Patch: [http://dwm.suckless.org/patches/transparency](http://dwm.suckless.org/patches/transparency)

Getting Errors during patch!

jacob@PwNz-BlackBox:~/dwm$ patch -p1 < dwm-transparency.diff
patching file config.def.h
Hunk #1 succeeded at 10 with fuzz 1.
patching file dwm.c
Hunk #1 FAILED at 58.
Hunk #2 succeeded at 95 (offset 2 lines).
Hunk #3 succeeded at 153 (offset 3 lines).
Hunk #4 succeeded at 184 (offset 3 lines).
Hunk #5 FAILED at 305.
Hunk #6 succeeded at 844 (offset 25 lines).
Hunk #7 succeeded at 879 (offset 25 lines).
Hunk #8 FAILED at 1124.
Hunk #9 succeeded at 1621 with fuzz 1 (offset 66 lines).
3 out of 9 hunks FAILED -- saving rejects to file dwm.c.rej


Note config.def.h is my unedited config file?!

---

