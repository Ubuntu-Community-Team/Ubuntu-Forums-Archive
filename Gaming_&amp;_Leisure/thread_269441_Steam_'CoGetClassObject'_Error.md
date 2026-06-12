---
title: "Steam 'CoGetClassObject' Error:"
date: 2006-10-01
forum: Gaming &amp; Leisure
---

### Post by underground3 on 2006-10-01
I have recently updated wine to version 0.9.22, and installed drivers for my ATI X300 card from the ati website (seems to have degraded appearance?) Now, when I run steam starting it from console, I get the following error:

john@john-laptop:~$ WINEDEBUG="fixme-all" wine Steam
wine: could not load L"c:\\windows\\system32\\Steam.exe": Module not found
john@john-laptop:~$
john@john-laptop:~$ WINEDEBUG="fixme-all" wine c:/Program\ Files/Steam/Steam.exeerr:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:systray:delete_icon invalid tray icon ID specified: 1d
Shutting down...

This causes Steam to freeze up almost as soon as it opened.  What should I do to fix this problem to allow me to play Counter Strike Source on Linux Ubuntu.

---

### Post by underground3 on 2006-10-01
Is anyone else who uses steam haveing troubles with the new update?
What should I do to fix this issure?

---

### Post by NeoRazorX on 2006-10-02
Better soluton is sign this petition to develop a Steam Linux client: [http://www.petitiononline.com/steam1/petition.html](http://www.petitiononline.com/steam1/petition.html)

---

