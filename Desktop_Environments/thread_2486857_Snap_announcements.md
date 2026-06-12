---
title: "Snap announcements"
date: 2023-05-14
forum: Desktop Environments
---

### Post by John_Carver on 2023-05-14
System announcements keep saying Snap is trying to load.

It never seems to get loaded plus I con't have a clue what it is?

---

### Post by #&amp;thj^% on 2023-05-14
Can you give this a try:
```
snap refresh snap-store --stable
```
Post back the return in Code Tags please.

---

### Post by John_Carver on 2023-05-14
$ snap refresh snap-store --stable
error: cannot refresh "snap-store": snap "snap-store" has running apps
       (snap-store), pids: 4764

---

### Post by #&amp;thj^% on 2023-05-14
OK Lets try this one more time:
```
sudo killall snap-store
sudo  snap refresh snap-store --stable
```
EDIT: Please be sure to close Gnome-Software as well.

---

### Post by John_Carver on 2023-05-14
john@john-desktop:~$ sudo killall snap-store
sudo  snap refresh snap-store --stable
[sudo] password for john: 
snap-store 41.3-71-g709398e from Canonical&#10003; refreshed
john@john-desktop:~$

---

### Post by #&amp;thj^% on 2023-05-14
That worked.
You do know what snaps are though right?

---

### Post by John_Carver on 2023-05-14
NO
I have just gotten back to Ubuntu after a few years off.
I installed it to a thumb drive in persistance mode 
Then a full install

---

### Post by #&amp;thj^% on 2023-05-14
Understood, this might help: [https://ubuntu.com/core/services/guide/snaps-intro](https://ubuntu.com/core/services/guide/snaps-intro)

---

### Post by John_Carver on 2023-05-14
[I]I'm reading about it now
[/I][https://ubuntu.com/core/services/guide/intro-ubuntu-core](https://ubuntu.com/core/services/guide/intro-ubuntu-core)

---

### Post by John_Carver on 2023-05-14
Lots to sink in
I'm 86 and it takes awhile
Thanks for your help

---

