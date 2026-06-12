---
title: "Xubuntu cdrom permissions - help needed"
date: 2006-09-23
forum: Desktop Environments
---

### Post by singedwings on 2006-09-23
I am having a problem playing music etc from my cdrom. Sound Juicer was reporting that it did not have permission to read the cdrom (hdc), so I solved this with:-
```
sudo chmod 777 /dev/hdc
```
However when I restart the computer the permissions revert to how they were before.

Is this the right way to solve this problem and how do I make the change permanent?

---

### Post by powder on 2006-09-23
Look in /etc/group and make sure your username appears next to the "cdrom" group.

---

### Post by singedwings on 2006-09-23
You are a star thank you, problem solved.:KS

---

### Post by powder on 2006-09-23
Cheers. :D

---

