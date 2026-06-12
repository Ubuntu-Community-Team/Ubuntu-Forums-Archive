---
title: "how to change the deault application to open mp3 files?"
date: 2009-03-03
forum: General Help
---

### Post by firsttimeuser on 2009-03-03
I installed amarok and want to use it as default mp3 player, but I don't see anywhere I can change this default system behavior.

---

### Post by dhughes on 2009-03-03
Right-click an mp3 file, select Properties and then in the Properties window that opens select the 'Open With' tab and choose from the list of applications.

---

### Post by mb_webguy on 2009-03-03
If you also want Amarok to automatically play audio CDs, open Nautilus (the File Manager) and go to Edit->Preferences->Media, and set CD Audio to Amarok.

---

### Post by mc4man on 2009-03-03
> If you also want Amarok to automatically play audio CDs, open Nautilus (the File Manager) and go to Edit->Preferences->Media, and set CD Audio to Amarok.

Just out of curiosity does that actually work for you on ubuntu 8.04 or 8.10

Only asking because while I've got amarok set to auto start *and* auto play cd's upon insertion from a cd drive(s) it would only work here if run from a script.
 (due to amarok needing "amarok --cdplay" for the auto play and that the location "/home/username/.gvfs/cdda mount on scdx" is unacceptable to amarok

---

### Post by mb_webguy on 2009-03-04
> **mc4man said:**
> Just out of curiosity does that actually work for you on ubuntu 8.04 or 8.10

Only asking because while I've got amarok set to auto start *and* auto play cd's upon insertion from a cd drive(s) it would only work here if run from a script.
 (due to amarok needing "amarok --cdplay" for the auto play and that the location "/home/username/.gvfs/cdda mount on scdx" is unacceptable to amarok

It works for me, but it seems like I might have edited the Amarok desktop file or else created a separate one specifically for CDs at some point to get it to work.  I'm not sure though, since it's been quite a while, if I did it at all.

---

