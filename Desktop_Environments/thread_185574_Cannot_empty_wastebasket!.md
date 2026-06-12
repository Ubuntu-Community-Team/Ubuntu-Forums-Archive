---
title: "Cannot empty wastebasket!?"
date: 2006-05-31
forum: Desktop Environments
---

### Post by Donshyoku on 2006-05-31
My wastebasket has 40 items in it right now and they won't go away.  They are everything I have deleted since installing Dapper from the RC1 CD a few days ago.  I can secondary-click and choose to Empty, but the windows clears (with no sound) and the wastebasket keeps all of its items?

I am up to date as of posting (nearly midnight on 31 May)... any ideas?

Thanks in advance!

---

### Post by aysiu on 2006-05-31
Can you paste these commands into a terminal and post the output back here? ```
cd ~/.Trash
ls
sudo rm -rf ~/.Trash/*
ls
```

---

### Post by user1397 on 2006-05-31
it's probably because there are files in there with root permissions, so you have to delete them using aysiu's way

---

### Post by Donshyoku on 2006-06-01
There was a root file in there and the command worked.

Thanks!

---

