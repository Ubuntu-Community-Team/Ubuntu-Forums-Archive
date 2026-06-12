---
title: "Desktop icons GONE"
date: 2009-06-25
forum: Desktop Environments
---

### Post by Daniel1994 on 2009-06-25
Yes, I know there are several threads about this subject already, but I could not find any that could help me. 

My desktop icons (launchers, files, trash, folders, mounted units etc.) are gone. All the time. I have tried typing nautilus in terminal but then this shows up :
[B]ERROR:nautilus-directory.c:611:add_to_hash_table: assertion failed: (g_hash_table_lookup (directory->details->file_hash, name) == NULL)
Aborted
[/B]Also there is a new folder inn my "Places" called **x-nautilus-desktop: trash**. I don't know if this has anything to do with my problem.

I'd appreciate any help.

Daniel

---

### Post by Daniel1994 on 2009-06-25
Nevermind, I solved this myself 30 sec after I added the thread. xD I feel really ridiculous right now.

For those with the same problem I had:
open terminal and simply run

```
sudo apt-get install nautilus
```
Funny I didn't think of that in the first place...

---

