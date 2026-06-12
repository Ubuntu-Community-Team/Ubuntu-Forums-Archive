---
title: "Disappearing filespace? Huge log files?"
date: 2010-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ajgenotti on 2010-05-12
Question. I've got a problem involving disappearing hard drive space. I deleted a ton of video files and music and the memory still hasn't returned. Did a disk usage scan and it says there's about 49 GB being used in my Log folder (/var/log). The only other large amount of memory usage is my music which has been downsized from 23 GB to 8.9 GB in two days to free up space. Anyone care to tell me what the deal is?

---

### Post by ajgenotti on 2010-05-12
Anyone? :(

---

### Post by gbrainin on 2010-05-12
That is enormous.  I just scanned my system, and /var is just a couple hundred MB.  /var/log is 13.2.

Have you done anything with your system recently, such as installing something?

---

### Post by gordintoronto on 2010-05-13
The logs are text files. You can edit them with gedit (the text editor)to see what messages your system is generating.

You could open Home Folder in Nautilus, then click on the up-arrow twice, then double-click on var, and double-click on log. Set it to List view to see the file sizes. You might need to view the "properties" of the folders to see where the disk space (not memory!) is being consumed.

---

### Post by BoneKracker on 2010-05-13
Alternatively, just open a terminal window and type
```
sudo du -h /var/log
```
Then post the results here.

To read how that du command works, read its man page (in the terminal, type)
```
man du
```

---

### Post by mgco on 2010-05-13
Just to make sure - perhaps the trash hasn't been emptied yet?

---

### Post by ajgenotti on 2010-05-13
Alright. Had a friend check it out. There was definitely nearly 50 GB of plain old log files floating around. Turns out, thanks to some firewall on here, that every package was getting logged. Yeah. All better now. Not sure what my friend did but it's all better.

---

