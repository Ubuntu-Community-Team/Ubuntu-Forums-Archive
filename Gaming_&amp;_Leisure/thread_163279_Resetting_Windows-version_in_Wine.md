---
title: "Resetting Windows-version in Wine"
date: 2006-04-20
forum: Gaming &amp; Leisure
---

### Post by kwaanens on 2006-04-20
I used winecfg and set up Windows 3.1 just to try something out. Now, nothing in Wine works. (Including winecfg) All I get is a message: 
```
MSVCRT.DLL for Win32
Error: MSVCRT.DLL is not compatible with Win32s.
```

Is there some config file I can manually change it back to XP or 2000?

Thanks!

- Ketil

Edit: Really weird, actually Google Earth works... But not iexplore or Firefox win edition.

---

### Post by DoktorSeven on 2006-04-20
Seems to change here in ~/.wine/user.reg:

```

[Software\\Wine] 
"Version"="****"

```

where **** is whatever windows version it emulates.  Change it to win2k for example.

---

### Post by kwaanens on 2006-04-20
[QUOTE=DoktorSeven]Seems to change here in ~/.wine/user.reg:

```

[Software\\Wine] 
"Version"="****"

```

where **** is whatever windows version it emulates.  Change it to win2k for example.[/QUOTE]

So is "win2k" the exact value for making it act like Windows 2000?

(There should be a comment with the various options in this file.)

- Ketil

---

