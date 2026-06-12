---
title: "Compiz and Emerald"
date: 2008-02-11
forum: Desktop Environments
---

### Post by reverend_HH on 2008-02-11
Hi everyone, I've taken a look at some other threads but they don't seem to apply to my problem. It seems that compiz or emerald just won't work. I've installed them before successfully but I upgraded my graphics card and installed the drivers from nvidia's website. Anytime that I enter emerald --replace i get this message in konsole:

```
 X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

When I enter compiz --replace I get this message in console:
```
compiz (core) - Warn: Unable to parse XML metadata from file "core.xml"
```

I don't get any of the effects, its as if I don't even have compiz installed but the borders do disappear. Somehow I think it might be something basic that I may have forgotten during install. If it helps, I used this as reference for install: [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion) I already added the option under the device section in the xorg.conf. Help is greatly appreciated!

Edit:
So I've done some more messing with it and I decided to try beryl and that seems to work just fine, the only problem is getting emerald to work. As of right now I'm using aquamarine but I would also like to have emerald enabled, it shows everything with no titlebars.

---

