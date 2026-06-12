---
title: "compiz is being a jerk..."
date: 2009-02-16
forum: General Help
---

### Post by Deutscher Alex on 2009-02-16
I can't edit anything on CompizConfig Settings Manager (ccsm)
This has been going on for a while, but I didn't really care because I felt I could live without the special effects. I was wrong.
After I upgraded to Intrepid, CCSM went back to default settings (Desktop cube off, Desktop wall on, etc.)
Trying to change settings in the ccsm program does nothing; it reverts back to default upon closing the program.
I tried going into gconf-editor and changing the keys for compiz there, but the active_plugins key is not writable.
I then tried changing it with the command gconftool, and received the error:
```
Error setting value: Can't overwrite existing read-only value: Value for `/apps/compiz/general/allscreens/options/active_plugins' set in a read-only source at the front of your configuration path
```
:mad:
I have tried reinstalling compiz, but to no avail. 
:-k

---

### Post by halovivek on 2009-02-16
try with sudo gconftool

---

### Post by Deutscher Alex on 2009-02-16
I did, and either way that would only change the configuration of root user



running compiz in terminal gave me, among other things:
```

*** glibc detected *** /usr/bin/compiz.real: double free or corruption (!prev): 0x088bc8d0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7abf454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7ac14b6]
/usr/lib/libGL.so.1[0xb7c270e1]
```

---

### Post by Deutscher Alex on 2009-02-16
*sigh*
bump

---

### Post by Twitch6000 on 2009-02-16
I have foudn that reinstalling compiz normally fixes this problem.

Also note compiz fusion is still beta(as far as I know)

---

### Post by Deutscher Alex on 2009-02-17
> **Twitch6000 said:**
> I have foudn that reinstalling compiz normally fixes this problem.

Also note compiz fusion is still beta(as far as I know)

I've already tried reinstalling compiz...
It worked perfectly before upgrading to Intrepid, and also works fine on an older computer I have that runs Intrepid.

---

### Post by Deutscher Alex on 2009-02-18
./bump
and I could have sworn i posted this under Desktop effects...
I guess it would fit more appropriately under General Help

---

### Post by Deutscher Alex on 2009-02-18
Solved...
in ccsm
Prefences > Backend > Flat-file Configuration Backend
instead of GConf Configuration Backend

anyone know what the command for the Flat-file backend is?

---

