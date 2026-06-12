---
title: "Files deleted (ending up in Trash)"
date: 2013-10-06
forum: Desktop Environments
---

### Post by svenskmand on 2013-10-06
I accidentially deleted my Documents folder in my home folder by pressing delete. To my surprise Ubuntu did not even ask me for a confirmation before moving the files to Trash.

I opened Trash and restored my files, but I am not sure all my files are restored as I do not remember the content of my Documents folder or its approximate size.

Are all my files restored?

PS: how can I make Ubuntu come with a confirmation box before deleting files (moving them to trash)?

PS^2: is there a max size limit of the Trash folder after which files are deleted?

Thanks for your help :)

---

### Post by Frogs Hair on 2013-10-06
The delete  options are in preferences > behavior on 13.04 . It seems to me that option was set by default, but I could be wrong not having used 12.10 for months .

---

### Post by svenskmand on 2013-10-06
If you mean the checkbox called "Ask before emptying the Trash or deleting files" in nautilus under Edit -> Preferences -> Behavior, then it is already checked :S

---

### Post by Frogs Hair on 2013-10-06
I get a caution prompt even though the file browser is set to bypass trash . As far as restoring your files they should be intact . Try restarting nautilus and then try deleting a junk document created in gedit or Libre office . ```
nautilus -q 
``` Next I would check the confirm trash setting dconf editor under Nautilus > Preferences.

---

### Post by svenskmand on 2013-10-07
Hmmm, I have nothing called Nautilus in dconf-editor :S Any idea how I can get it back there?

---

### Post by mc4man on 2013-10-07
You only can get confirmation when using "delete" from the nautilus context menu or when using shift+delete  (and then the file is actually deleted, no trash
If you highlight a file & press the delete key then it goes immediately to trash

---

