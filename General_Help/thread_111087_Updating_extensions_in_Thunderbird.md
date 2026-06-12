---
title: "Updating extensions in Thunderbird"
date: 2006-01-01
forum: General Help
---

### Post by kwaanens on 2006-01-01
Unlike Firefox, *"Edit" > "Preferences" > Check for updates to extensions* in Thunderbird actually seems to do something useful.
However, when I restart the program the extensions haven't been updated anyway.

I tried in console, to see if that made a difference. First run of program:

> $ mozilla-thunderbird
selected locale: en-US
observe:
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 ** * loading the extensions datasource

I try to update the extensions. Then close, then restart:

> $ mozilla-thunderbird
selected locale: en-US
 ***** Registering: Clean Compreg! ****
observe:
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 ** * loading the extensions datasource
*** ExtensionManager:_updateManifests: no access privileges to application direc tory, skipping.
 ***** Registering: Clean Compreg! ****
observe:
nothing here: null
observe called
FILE: [xpconnect wrapped nsIFile]DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 ** * loading the extensions datasource
*** ExtensionManager:_updateManifests: no access privileges to application direc tory, skipping.

Any clues?

- Ketil

---

### Post by ape on 2006-01-05
I'm seeing this same problem.  I can add new extensions just fine and I can uninstall them.  But when I try to even add in a newer version of the extension that I removed, I too, get the old information back in the extensions dialog. 

Any headway?

---

