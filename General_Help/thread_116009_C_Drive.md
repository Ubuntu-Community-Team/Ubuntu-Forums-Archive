---
title: "C Drive"
date: 2006-01-11
forum: General Help
---

### Post by Y-town on 2006-01-11
How can i access the C drive?

---

### Post by kaamos on 2006-01-11
Do you mean with wine? It is in /home/username/.wine/drive_c/

---

### Post by Y-town on 2006-01-11
yes, but i have no folder called .wine in my user account folder.

---

### Post by kaamos on 2006-01-11
It is a hidden folder since it starts with a dot. Press ctrl+h to show hidden files and folders.

---

### Post by Mr_Grieves on 2006-01-11
I think perhaps Y-Town is asking if he can access his Windows partition in Linux..

If this is what you wonder, read this: [http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)
If you don't want to mount the partition permenently as told.. I just happen to write a little script that does it automaticly for you. Check this out: [http://winm.hacka.net](http://winm.hacka.net)

If you are really wondering about Wine ( [http://www.winehq.com](http://www.winehq.com) ) then open up a terminal and type:
```

ls -a | grep wine

```
That should give you this:
```

.wine

```
If not.. I guess it's like I first wrote.

---

