---
title: "Can't install mathplayer on wine"
date: 2009-01-09
forum: Education &amp; Science
---

### Post by enginuysal on 2009-01-09
I need to use ie 6 for my universty's online learning management system and I need "mathplayer" with it in order to see math equations.

I installed ie6 via ies4linux and it works without any problem.

When I try to install mathplayer.exe via wine, it gives an error at the and and quits installation. The error is also logged in a file. I'm pasting the last part below;

```
Start: Register DLL {

	DLL path = 'C:\Program Files\Design Science\MathPlayer\MathPlayer.dll'

	Success (Ok, 0x00000200): Load DLL

	Success (Ok, 0x00000200): Register DLL

} End: Register DLL





Start: Register DLL {

	DLL path = 'C:\Program Files\Design Science\MathPlayer\MathMLMimer.dll'

	Success (Ok, 0x00000200): Load DLL

	Failure (Failure, 0x80000200): Register DLL

} End: Register DLL



Failure: Unable to register MathMLMimer

Installation failed!

Exit code = 'exitOk' (0).



MathPlayer log ends (error count = 2).

```

My distro is ubuntu 8.10 and the version of wine ie6 is running on is 1.0.1.

Any help/idea is appreciated,

Engin Uysal

---

