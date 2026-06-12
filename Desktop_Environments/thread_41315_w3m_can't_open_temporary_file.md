---
title: "w3m can't open temporary file"
date: 2005-06-12
forum: Desktop Environments
---

### Post by alive on 2005-06-12
I decided to try w3m for an alternative web browsing experience; however, when I attempt to edit a textarea field, I get "Can't open temporary file" and am thereby prevented from editing. Any suggestions?

---

### Post by eyequeue on 2005-06-12
[QUOTE=alive]I decided to try w3m for an alternative web browsing experience; however, when I attempt to edit a textarea field, I get "Can't open temporary file" and am thereby prevented from editing. Any suggestions?[/QUOTE]

I don't run into the same here.

Perhaps you have run out of drive space on whatever partition holds /tmp or /home?

Does the output of
```
$ df
```
show any partition at 100% usage?

---

### Post by alive on 2005-06-13
Nope. All the partitions have plenty of room.

w3m also says "Can't open history" when it quits.

---

