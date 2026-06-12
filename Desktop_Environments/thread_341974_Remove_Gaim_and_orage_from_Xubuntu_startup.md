---
title: "Remove Gaim and orage from Xubuntu startup?"
date: 2007-01-19
forum: Desktop Environments
---

### Post by camini on 2007-01-19
This is my first post here, so apologies if this is a trivial one..

Orage and Gaim Internet messenger seem to start up every time I start xubuntu.

How can I stop these from starting automatically?  I don't mind having these on my system but would like to reduce boot time to a max.

Anything else I can do to optimize boot process & how?

---

### Post by camini on 2007-01-20
Bump. Too simple?

---

### Post by kerry_s on 2007-01-20
Open a terminal and run> killall gaim <and> killall orage , then logout and back in.

Unless you put them in your auto started apps?

---

### Post by camini on 2007-01-20
Ok I'll try killall although it sounds pretty drastic.  I will look up the man pages for killall as it's not found in my familiar Unix vocabulary..

I suspect it's in my startup list but don't know how to access or where to find this list of startup apps..  somewhat frustrating :o)

---

### Post by Pobega on 2007-01-20
killall just ends the process, when you restart it will just start again. 

To take it off of the autostarted applications, go to Applications->Settings->Autostarted Applications and remove Gaim and Orage from there.

---

### Post by camini on 2007-01-20
Cool, thanks to all.
In the end it was:
- me overlooking the 'Autostarted applications' entry in the settings menu, because it doesn't have an icon.  The autostart section was empty also.
- some order problem with the 'autosave session on logout', that apparently made these applications come back every time I logged in..

---

### Post by Pobega on 2007-01-20
> **camini said:**
> Cool, thanks to all.
In the end it was:
- me overlooking the 'Autostarted applications' entry in the settings menu, because it doesn't have an icon.  The autostart section was empty also.
- some order problem with the 'autosave session on logout', that apparently made these applications come back every time I logged in..

Personally I disabled the session autosaving, it ends up just annoying me when I have games and apps popping up right when I start up.

---

