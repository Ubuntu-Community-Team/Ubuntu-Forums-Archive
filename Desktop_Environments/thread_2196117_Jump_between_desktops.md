---
title: "Jump between desktops"
date: 2013-12-28
forum: Desktop Environments
---

### Post by mayagrafix on 2013-12-28
How can I share a doc I created in Desktop "A" (or User #1) with another person on Desktop "B" (or User#2) on the same computer. Should I use Account instead of Desktop?

Thanks for ur input :KS

---

### Post by Tristan_Williams on 2013-12-28
There are lots of ways to do this, but Heres the way I do it.

In the /home directory (the one that lists all of the computers users) make a folder named "Public"

Now, inside of that folder, make Documents, Music, Pictures, and Videos folders (You can omit any of these, or all of them)

Open a terminal, and issue the following command:
```

sudo chmod -R ugo+rwx /home/Publuc

```

Now, anyone can put their files into that folder.

Note: You may have to change the permissions of each file when you put new files into the folder.

---

