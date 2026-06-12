---
title: "Help on running C&amp;C Generals"
date: 2007-03-01
forum: Gaming &amp; Leisure
---

### Post by evaarties on 2007-03-01
I managed to install C&C Generals 1.07 but I have the following problems running it with Wine 0.9.30:

Running ./generals_code gives me:

> wine: could not load L"c:\\windows\\system32\\Generals_Code.exe": Module not found
13607: oude prioriteit 0, nieuwe prioriteit 5


And running ./generals starts the game but I can't get it active with my mouse or keyboard. Sounds works though.

I edited the files ./generals and ./generals_code to use:

```
#!/bin/bash
```

instead of

```
#!/bin/sh
```

since I'm using Ubuntu Edgy Eft.

Someone who had the same problems and managed to fix them?

PS I ran this script to install needed packages: [http://kegel.com/wine/edgy.sh](http://kegel.com/wine/edgy.sh) found at [http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages).

PSS If someone knows how to install patch 1.08, please share it with me.

---

### Post by evaarties on 2007-03-03
Someone?

---

