---
title: "problem with winecfg crashing"
date: 2006-01-07
forum: General Help
---

### Post by DaveRowell on 2006-01-07
Using Synaptic I installed the 20050725 version of wine, libwine, wine-dev, libwine-dev
If I run wine - it does ;-)
If I run winecfg - it doesn't! ;-( and I get this error message:

david@CPQ1265:~$ winecfg
err:thunk:_loadthunk (commctrl.dll, Cctl1632_ThunkData16, comctl32.dll): Unable to load 'commctrl.dll', error 2
err:module:LdrInitializeThunk "comctl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\winecfg.exe" failed, status c0000142
david@CPQ1265:~$

I take it that the message says that commctrl.dll doesn't exist and that it's needed so winecfg couldn't start.
How can I fix this problem?

---

### Post by dcstar on 2006-01-07
[QUOTE=DaveRowell]Using Synaptic I installed the 20050725 version of wine, libwine, wine-dev, libwine-dev
If I run wine - it does ;-)
If I run winecfg - it doesn't! ;-( and I get this error message:

david@CPQ1265:~$ winecfg
err:thunk:_loadthunk (commctrl.dll, Cctl1632_ThunkData16, comctl32.dll): Unable to load 'commctrl.dll', error 2
err:module:LdrInitializeThunk "comctl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\winecfg.exe" failed, status c0000142
david@CPQ1265:~$

I take it that the message says that commctrl.dll doesn't exist and that it's needed so winecfg couldn't start.
How can I fix this problem?[/QUOTE]
Rename your (hidden) .wine directory to something else, and then try to run it again.

---

### Post by DaveRowell on 2006-01-07
David - thanks a million!  :D 

If, as you say "Knowledge is a measure of how many answers you have, intelligence is a measure of how many questions you have."  I gotta be a mensa candidate!!! ;)

---

### Post by dcstar on 2006-01-08
[QUOTE=DaveRowell]David - thanks a million!  :D

If, as you say "Knowledge is a measure of how many answers you have, intelligence is a measure of how many questions you have."  I gotta be a mensa candidate!!! ;)[/QUOTE]
You and me both.....          ;)

BTW, the .wine directory contains your wine configuration, so if you install Windows software that is where all the registry stuff goes, and if you have to rename it again you have to re-install everything......      :(

---

