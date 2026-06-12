---
title: "Compiz fusion on upstart"
date: 2007-07-13
forum: Desktop Effects &amp; Customization
---

### Post by czepluch on 2007-07-13
Hi.

some times when i startup ubuntu emerald, and sometimes compiz fusion just disables. I've done the session and set : 
compiz --replace
compiz --replace -c emerald &
compiz  --indirect-rendering --replace

Those are the programs that startup.

It also often disables when i open firefox or another program as the first program since booting. Why does it do that ?

:)

---

### Post by bdtgp on 2007-07-13
It may be because you are trying to start/replace compiz like three times.
```
compiz --replace -c emerald &
```
If you need the indirect rendering one that use that too.  Just don't do compiz --replace and the emerald one.

---

### Post by czepluch on 2007-07-13
> **bdtgp said:**
> It may be because you are trying to start/replace compiz like three times.
```
compiz --replace -c emerald &
```
If you need the indirect rendering one that use that too.  Just don't do compiz --replace and the emerald one.

So what should i have on startup?

---

### Post by czepluch on 2007-07-13
bump

---

### Post by hyperair on 2007-07-13
Just have ```
compiz --replace
``` there. If it doesn't work, then post back here or try another. xD

---

### Post by bdtgp on 2007-07-13
if you want the emerald themes to start too then have this:
```
compiz --replace -c emerald &
```

---

### Post by hyperair on 2007-07-13
As of the current version of Compiz Fusion, I realized that the "-c emerald" is no longer necessary to load emerald. Maybe that's because my decoration plugin has the command field set to "emerald --replace". Anyway it's a suggestion. =) Saves on typing.

---

