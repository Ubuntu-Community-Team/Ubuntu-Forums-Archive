---
title: "Trying to Get Halo To run in wine"
date: 2007-06-15
forum: Gaming &amp; Leisure
---

### Post by kdarkentity on 2007-06-15
i installed halo from the cd using wine but i do not think i have the right .dlls or for whatever reason im missing somthing

here is the output from the terminal when i try running halo.exe with wine 

err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135

---

### Post by DracoPsycho on 2007-06-15
[http://appdb.winehq.org/appview.php?iVersionId=2720]("http://appdb.winehq.org/appview.php?iVersionId=2720")

There is a Wine AppDB entry about Halo, it's coloured gold with wine CVS so it should play smooth. There are also installation instructions there, maybe they'll help.

---

### Post by kdarkentity on 2007-06-15
thanks ...i have looked at this site before but i cant quite figure out what to do ...could you refer me to the installation instructions?

---

### Post by DracoPsycho on 2007-06-18
I didn't try to install Halo myself, and this site is everything I found. From what I see now, it has been downgraded to Bronze because there are some graphical issues and part of the game is unplayable... Sorry, can't help much more :)

---

