---
title: "Can't delete item in Trash"
date: 2009-02-03
forum: General Help
---

### Post by joey-elijah on 2009-02-03
I have an item i don't "own" (pfft!) in the trash Not sure why i don't since it was just an image downloaded from Firefox... 

Anyway, I browsed the forum and followed both entering sudo nautilus and trying - it said i didn't have access to the trash, and i followed a command given in a forum post that other's said worked fine, but actualyl deleted all the files in my home folder :( 

How do i get rid of this file?

---

### Post by taurus on 2009-02-03
Assuming you are in the directory where that file is, you could run

```
sudo rm *filename*
```

---

### Post by icanfly0307 on 2009-02-03
Try logging in as root and then deleting the file.

---

