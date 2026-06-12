---
title: "Halo with wine terminal output"
date: 2007-06-17
forum: Gaming &amp; Leisure
---

### Post by kdarkentity on 2007-06-17
when i try running halo.exe with wine thru the terminal i get this output

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture

is this a problem?

---

### Post by cogadh on 2007-06-18
No, it's a reference to an unimplemented Direct Sound option in Wine. It doesn't actually affect anything.

---

### Post by kdarkentity on 2007-06-18
oh alright thanks

---

### Post by GMU_DodgyHodgy on 2007-06-19
> **cogadh said:**
> No, it's a reference to an unimplemented Direct Sound option in Wine. It doesn't actually affect anything.


Does Halo actually work with Wine???

---

### Post by lordhebe on 2007-06-19
Yep! Check here: [http://appdb.winehq.org/appview.php?iVersionId=2720]("http://appdb.winehq.org/appview.php?iVersionId=2720")

Here is an already active thread on the subject [http://ubuntuforums.org/showthread.php?t=473843]("http://ubuntuforums.org/showthread.php?t=473843") in which 2 people (including yours truly) have been able to get it working, however it seems to have exposed some possible problems with ATI cards. I've also posted some screen shots.

---

### Post by kdarkentity on 2007-06-19
on one of your other posts on the other thread you said that you had the following threads on the end of your desktop shortcut ...is this nessacery and how do i apply them??

these are the flags i am reffering to

-novideo -vidmode 1024,768,60 -use11

---

### Post by lordhebe on 2007-06-19
The only one that is necessary is the -novideo one, because (for me anyway) the game crashes when the company videos play. Adding  -novideo skips them and goes straight to the main menu, meaning it's possible to play. The other ones are my -vidmode is simply applying my preferred resolution and -use11 is my recomendation, I found I got best performance and visuals out of this. You apply them  by adding them to a shortcut (or a command line input after the .exe file. Here's an example (from my halo shortcut) ```
env WINEPREFIX="/home/chris/.wine" wine "C:\Program Files\Microsoft Games\Halo\HALO.EXE" -novideo -vidmode 1024,768,60 -use11
```

---

