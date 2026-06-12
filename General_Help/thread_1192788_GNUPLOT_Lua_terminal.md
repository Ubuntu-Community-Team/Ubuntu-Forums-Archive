---
title: "GNUPLOT Lua terminal"
date: 2009-06-20
forum: General Help
---

### Post by Timtro on 2009-06-20
Hi All,

Thanks in advance.

Yesterday I downloaded and compiled the CVS version of GNUPLOT. I had to apt-get Lua, and follow the instructions here

[http://ubuntuforums.org/showthread.php?t=1127979](http://ubuntuforums.org/showthread.php?t=1127979)

to get the configure script to pick it up. Compilation seems to go fine, but when I try to set the terminal:
```

gnuplot> set term lua
Terminal type set to 'lua'
         No Lua driver name or file name given!

```

I checked the config.log, and there's a bunch of nonsense about not finding lua.h. I'm not sure why, since
```

pkg-config --cflags "lua"
-I/usr/include/lua5.1

```

Anyhow, the -I flag shows up fine in CPPFLAGS in the Makefile, but I don't know if it's being picked up or not by GCC.

Could anyone point me in the right direction?

Thanks,



Tim.

---

### Post by Timtro on 2009-06-20
Okay, I've got it figured out.

None of that lua.h stuff was an issue. The issue is that there was a naming change. To start the lua terminal with tikz, you have to:

set term lua tikz

to let it know you want the tikz extension to the lua terminal. This paves the way for other lua based terminals, not just the tikz output.

---

