---
title: "Recover lost text - gedit"
date: 2009-02-05
forum: General Help
---

### Post by tehforum on 2009-02-05
Hi,

I had some important text in the Text Editor Applications > Accessories > Text Editor. I am running Ubuntu 7.10 Gutsy Gibbon. I need to recover that text, but I quit the program without saving, so I'm stuck for any idea.s

Thanks for your help. :D

---

### Post by niteshifter on 2009-02-05
Hi,

Text Editor (Gedit) makes a backup copy of the file using the filename and sticking a ~ on the end. If you had done a save prior to the last session of edits that you didn't save, you might be able to recover from that backup file.

Note that files ending with a ~ are "hidden" files, you need to use Ctrl+H to see them in File Browser (Nautilus) or open a terminal in the folder you were working and:
```
ls -al *~
```

If you didn't do a save somewhere along the line, you're out of luck. That text was in memory and is long gone.

---

### Post by tehforum on 2009-02-08
AH OK, I'm afraid I didn't save my document. But my lesson is learned, and incase I accidentally close gedit, I will refer to your post again.

Thanks.

---

