---
title: "hard drives magicaly changing names???"
date: 2009-01-12
forum: General Help
---

### Post by b0b138 on 2009-01-12
I've got 3 disks, 1 80g and 2 500g. / is on the 80g and /home is one of the 500g. For the longest time, from gutsy to intrepid, my 80g has always been sdc (even though its plugged into the slot for drive 0, a 500g plugged into slot for drive 1, and the other 500g drive 2. I've never known why, but a learned to accept it, no problem.) /home has been sdb and the other sda.

Well it has suddenly decided to change things, and is now calling / sda, /home sdc, and the other drive is sdb. Everything is apparently still working (fstab references UUID's),but....WTF????????

---

### Post by sdennie on 2009-01-12
This was the very reason UUIDs were invented.  They should be fixed names and not based on arbitrary OS assignment or BIOS naming.

---

### Post by dr_rimzi on 2009-01-12
I dunno, but for me, UUIDs cause much more problems than the standart names (sda, etc.) Especially when i keep installing new OSs alongside ubuntu. Anybody know how it (UUID) is formed?

---

