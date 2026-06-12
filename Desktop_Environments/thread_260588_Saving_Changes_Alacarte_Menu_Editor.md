---
title: "Saving Changes: Alacarte Menu Editor"
date: 2006-09-19
forum: Desktop Environments
---

### Post by 3370318 on 2006-09-19
By default, Alacarte does not retain changes to menus (which should be saved upon closing Alacarte).  I know that there is some way to fix this problem, but I cannot find any useful information.  Could someone be so kind as to point be to the right thread or provide an answer?

Thanks

---

### Post by Poeffie on 2006-09-19
Strange, normally you should just click "close" (and not "revert") and the changes will automatically be saved.

---

### Post by 3370318 on 2006-09-19
My problem appears to be more general than just Alacarte.  It seems that I cannot change file associations through nautilus either (for example, I cannot associate MP3s with xmms).  I have tried editing menus and changing associations as root, but without any luck.

I seem to remember having to edit some config file somewhere with a previous install in order to get these things to work, but I forgot which file I edited.  Does anybody out there have any answers?

Thanks

---

### Post by 3370318 on 2006-09-23
I finally found the solution to both of these problems.  Apparently, .local in my home directory was owned by root.  In order to reset file associations and edit menus, simply remove .local as root.

---

### Post by srt4play on 2006-09-29
I had the same problem, many thanks for posting the solution!

---

