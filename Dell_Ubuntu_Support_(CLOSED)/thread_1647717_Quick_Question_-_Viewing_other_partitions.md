---
title: "Quick Question - Viewing other partitions"
date: 2010-12-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by seekingelysium on 2010-12-17
I know that in windows when the computer started up I could press F8 and the system screen would come up about safe mode and viewing other partitions, but when I press F8 with ubuntu nothing happens. I just want to see if my old version of windows xp is still on the other partition of my computer. How do I do this. I have a dell dimension 3000.

---

### Post by Linux_junkie on 2010-12-17
You should be able to view your Windows partition through the Nautilus file browser by selecting the partition (drive) from the list on the left hand side of the window.  Hope this helps.

---

### Post by seekingelysium on 2010-12-18
I found a way to view my partitions and now I'm confused about something else. I should only have ubuntu installed on my computer but both partitions have something on them. One says that it has something with like 15,000 mb on it and the other has something with only like 700 something. Does anyone know why it might be like that? I want to use the second partition but I don't want to erase anything.

---

### Post by squenson on 2010-12-18
Could the 700 MB partition be your swap partition?

---

### Post by ugm6hr on 2010-12-19
Post the output from:
```
sudo fdisk -l
```

---

