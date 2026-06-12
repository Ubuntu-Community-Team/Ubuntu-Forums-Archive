---
title: "cedega or wine..."
date: 2006-08-16
forum: Gaming &amp; Leisure
---

### Post by Mooie on 2006-08-16
Will I get the same preformance in wine that I get in cedega on warcraft3, world of warcraft, steam games, and diablo2?  they are all supported by wine.    also, if it makes any difference, I use 64-bit ubuntu (I have wine 9.19 installed)

---

### Post by Mooie on 2006-08-16
If I copy my system and system32 files from my winblows partition into the wine c drive, would it mess anything up?  Should I overwrite the wine dll files, or replace them?

---

### Post by Polygon on 2006-08-16
there is suppost to be a way to use the native windows .dll files ntead of wine's version, im not sure if thats the way though. maybe check winehq.com to see how you use the native windows dll files instead of the wine ones.

---

### Post by goatflyer on 2006-08-16
To choose native(real) .dll files rather than the wine builtins, run winecfg from the terminal, select the dll libraries tab, select the name of the dll file from the list (these are the only 'builtin' ones --- some of which are just stubs).  Lastly choose the order 'native, builtin'.

Be sure the native .dll file is in your wine's windows/system (or system32) directory.

THIS BEING SAID -- if the game is working for you using the wine builtins I would NOT replace the dlls for the native windows files.  Too many things could break.

---

### Post by Mooie on 2006-08-17
oh, thanks, i will try that.  nothing is really working w/ wine as is, so it cant screw much up, lol

---

