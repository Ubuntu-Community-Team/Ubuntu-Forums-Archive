---
title: "gedit can't read a file but cat can???"
date: 2009-02-21
forum: General Help
---

### Post by Nathan_M on 2009-02-21
I would've thought gedit would be a bit more sophisticated in handling text files than cat, but apparently not. In gedit, notes that I made on my phone come out as lots of funny characters... although some of them don't come out at all. If I use cat, the text is reproduces perfectly. Does anyone have any suggestions as to how I can make these work in gedit? I've attached one for your reference.

---

### Post by kushal.7 on 2009-02-21
don't know about ans... but this works fine with vi editor...

---

### Post by mrphd on 2009-02-21
The last character in your text file is a null character (00 in hexadecimal) which is why gedit is having problems with it, as it seems to be getting confused with the character encoding. If this last character is replaced with a line feed (0A) then it will work without problem.

---

### Post by heindsight on 2009-02-21
I've done some checking and it seems the problem is that the file ends in a NULL character which apparently confuses gedit.

Try doing
```
tr '\000' '\n' < Nokia.txt > nokia_fixed.txt
```
That will replace NULL characters with newlines and gedit should have no problems with the file anymore.

---

### Post by Yashiro on 2009-02-21
Yep. Gedit seems to fail at reading the encoding on this file.
Cat and Firefox can read it.

Open it in Firefox and cut and paste manually into gedit for now. Or run the shell commands above to strip the null character at the end.

---

### Post by Nathan_M on 2009-02-23
Thanks everybody.

---

