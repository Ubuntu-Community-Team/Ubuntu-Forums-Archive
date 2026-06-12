---
title: "Thunderbird won't run"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Abiezer on 2005-10-13
After upgrading Thunderbird won't run. Attempting to run from a terminal I get this:

```
selected locale: en-US
observe:
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]/usr/lib/mozilla-thunderbird/run-mozilla.sh: li ne 159: 11620 Segmentation fault      "$prog" ${1+"$@"}
```

Any help or suggestions appreciated

---

### Post by kassetra on 2005-10-13
[QUOTE=Abiezer]After upgrading Thunderbird won't run. Attempting to run from a terminal I get this:

```
selected locale: en-US
observe:
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]/usr/lib/mozilla-thunderbird/run-mozilla.sh: li ne 159: 11620 Segmentation fault      "$prog" ${1+"$@"}
```

Any help or suggestions appreciated[/QUOTE]

Did you install thunderbird from Synaptic or did you compile/build it yourself?  If you have done it yourself, you will need to recompile it for your new libraries.

If you upgraded via Synaptic, it is very possible that your old settings are incompatible with the new version - if that is the case, move your thunderbird directory to your desktop or anywhere other than where it currently resides and restart thunderbird.  You will need to import your mail back into thunderbird from wherever you moved your old directory to.

---

### Post by Abiezer on 2005-10-13
Thanks - I seem somehow to have kept the old version - a check of Synaptic showed that I still was using the 5.04 one for some reason. A partial uninstall/re-install sorted it all out and it's now using the Breezy package.

---

