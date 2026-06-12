---
title: "Edgy,wine and keyboard input"
date: 2006-10-28
forum: Gaming &amp; Leisure
---

### Post by lotheac on 2006-10-28
I recently upgraded to Edgy (and more recently did a clean install, didn't change a thing though) and using Wine, I can't input accented characters (äöå). This worked like a charm in Dapper, and I'm using the exact same wine version (though it wouldn't work with 0.9.23 deb from winehq either). I've tried "LC_ALL=fi_FI.ISO-8859-1 wine notepad" but that doesn't change anything.

I have absolutely no clue where the problem could be and since I did a clean install this thread's purpose is more to ask if anyone else has this problem.

edit:
I tried starting an unrelated application that uses Qt in terminal and it tells me "Locales not supported by X server". Could this have something to do with it? Seems a bit odd though seeing that my locales work fine elsewhere. Then again the application I tried was 32bit and so is wine, and I'm on AMD64.

---

### Post by theh0g on 2006-10-28
Bump.

---

### Post by lotheac on 2006-10-28
I take it that means you have this problem as well. Happy to hear :D

---

