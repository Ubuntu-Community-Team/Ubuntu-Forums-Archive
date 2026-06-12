---
title: "Problem with CAPS named dirs!"
date: 2005-05-01
forum: Desktop Environments
---

### Post by coldturkey on 2005-05-01
I converted my 200GB harddisc to FAT32 but lately I've had some problem with it.
Each time I create a new dir and change its name to one with CAPS letter, eg: COLDPRIV, a new dir with the same name but the letter in small is created. Whenever I move/close/change dir, the dir with CAPS letters dissapers. If I delete of them, they both dissaper.

It's really annoying, could somebody help me :)? Whats the problem?

---

### Post by nad on 2005-05-01
The default option for a mounted vfat file system is to display short file names (8.3) as all lower case. If the name is longer, it will display as given. See man mount for vfat mount options.

---

