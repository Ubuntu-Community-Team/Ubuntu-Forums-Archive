---
title: "Accidental File deletion in Ubuntu"
date: 2009-02-05
forum: General Help
---

### Post by Ionna on 2009-02-05
While deleting a folder in my external, I accidentally deleted another folder after that, and only realised it when Ubuntu said they were deleting a thousand files (it was my music folder and I had pressed enter without realising I'd selected the wrong folder). It was too late to press cancel, so I'm wondering, is there a way for me to retrieve those files back?

I'm on eeeBuntu on the eeePC if that helps. 

Many thanks in advance. And CTRL Z doesn't work (Windows behaviour, I know).

---

### Post by evilempire on 2009-02-05
What filesystem are you using? assuming that it's the default EXT3, here's an article describing how it's done. 

[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

Unfortunately it sounds like EXT3 is really hard to recover deleted files from  :(

---

### Post by gackt on 2009-02-05
Have you try to look into Trash?

---

### Post by Ionna on 2009-02-05
Thanks for the link! I just skimmed it through, and it looks like it's a program but I'm not sure if it will work, because I think the external is FAT32. :s

---

### Post by Ionna on 2009-02-05
Yes, I did, Gackt, but they were not there. :s

---

### Post by cariboo on 2009-02-05
Have a look at [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk"). It should be able to recover most of your files. Testdisk is in the repositories.

I guess now would be a good time to consider a good backup strategy.

Jim

---

### Post by Ionna on 2009-02-05
Thanks Jim!

Actually this is the backup (which needs to be updated) which I usually leave in the office. :3

---

### Post by gackt on 2009-02-17
Well probably u should try to recover it in windows using windows software  (there are many of it I'm sure) but in my experience bringing back a file larger than 3mb is not always perfect.

---

