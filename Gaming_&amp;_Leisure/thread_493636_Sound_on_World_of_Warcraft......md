---
title: "Sound on World of Warcraft....."
date: 2007-07-05
forum: Gaming &amp; Leisure
---

### Post by Haz13r on 2007-07-05
Hey, i got World of Warcraft working PERFECTLY with wine.  The only problem is the sound issue.  I have this thread which helped me tons and the only part im left with is aoss wine /path-to-program/WoW.exe. I typed in the path-to-program which was
aoss wine /home/thomas/.wine/drive_c/Program Files/World of Warcraft.WoW.exe but it just didnt work, all it said was that there was no such Directory.  Cand someone help?

---

### Post by Cappy on 2007-07-06
```
aoss wine "~/.wine/drive_c/Program Files/World of Warcraft/WoW.exe"
```
(there was a space in there so you need either quotations or a backslash before each space)
It's case sensitive too. If you actually type it out (instead of copying and pasting it), use TAB to complete the folder/directory names and it will be much much easier.

---

### Post by Haz13r on 2007-07-06
aoss wine "~/.wine/drive_c/Program Files/World of Warcraft/WoW.exe"
Doesnt work but i replaced the ~ with 
/home/thomas and then it worked.  Thanks!

---

### Post by Haz13r on 2007-07-06
Well that thing works but i still hear no sound whats so ever.  
I found this thing config.wtf and it told me to put in SET SoundBufferSize 100 or a number inbetween 50 and 250.  Can some one help?

---

### Post by Haz13r on 2007-07-06
Got it, it told me to type this in

SET SoundOutputSystem "1"
SET SoundBufferSize "150"

---

