---
title: "conduit: tomboy not syncing with google docs"
date: 2009-06-08
forum: General Help
---

### Post by oimon on 2009-06-08
hello
thought i would try out conduit for syncing notes to google docs. I would rather not setup dropbox, ubuntu One etc (for various reasons), but the process doesn't seem to work

Using conduit 0.3.15 on jaunty

Also there appears a grey text "synchronization skipped" under the google docs box in the conduit panel
conduit.log:
modules.Tomboy      ][DEBUG  ] Getting note: note://tomboy/xxxx (TomboyModule.py:170)
[Syncronization      ][DEBUG  ] 1WAY PUT: Tomboy Notes (note://tomboy/xxxx) -----> Google 
Documents (Synchronization.py:489)
[datatypes.DataType  ][DEBUG  ] Getting Rid for note://tomboy/xxxx(removed) (DataType.py:151)
[TypeConverter       ][DEBUG  ] Convert note/tomboy ->  using [('note', '', {})] (TypeConverter.py:209)
[TypeConverter       ][DEBUG  ] Conversions note ->  doesnt exist (TypeConverter.py:191)
[Syncronization      ][WARNING] Error performing conversion:
No conversion exists: note/tomboy ->  (Synchronization.py:357)

So it seems that note/tomboy conversion doesn't exist. I can sync to a backup folder, but not to google docs. Anyone else trying to do this? I though this was one of the main features of conduit.

---

### Post by insanity54 on 2009-07-30
I'm having the same problem. I'm trying to synchronize tomboy notes with Google Documents. When I attempt to sync the two, I get a "100% complete" message, with a "Synchronization OK" message under tomboy, and a "Synchronization Skipped" under Google Documents.

---

### Post by dunbrokin on 2009-08-16
Same problem, I have been trying all day to sync some documents with Google Docs...and while I get the 100% complete message....but there is no transfer....I think this program is bust.

---

### Post by scumie on 2009-11-04
Same problem here. Would love if someone got a solution for this.

---

### Post by twqqis on 2010-08-31
anyone been able to sync tomboy to google docs yet?

---

### Post by oimon on 2010-10-28
since ubuntu one and tomboy started offering a decent sync service i use that instead, it offers what i need.
i can even run a read-only tomdroid app on my android phone to sync and display notes i've written on my pc.

---

