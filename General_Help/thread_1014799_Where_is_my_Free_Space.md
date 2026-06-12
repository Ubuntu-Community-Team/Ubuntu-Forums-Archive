---
title: "Where is my Free Space?"
date: 2008-12-18
forum: General Help
---

### Post by azathrael on 2008-12-18
I have 2 HDDs on my laptop and I installed Ubuntu on one and just recently turned the other into a storage folder.

My storage folder has around 130GB of free space, and the HDD that has Ubuntu installed on SHOULD have about 7GB of free space left (according to the Disk Usage Analyzer), except when I go to my folder, right click, properties, and look at Free Space, it's at 0!!! I tried to record a speech using Sound Recorder but whenever I press record it says "No space left on the resource".

Where is all my free space and why can't Ubuntu recognize it!?!?

Thanks.

---

### Post by albandy on 2008-12-18
Maybe you have a partition for /home and is full.

---

### Post by Izek on 2008-12-18
Tell us the output of

**df -h**

in terminal

---

### Post by linux_tech on 2008-12-18
If you open your home folder in the file browser, how much free space is listed at the bottom?

---

### Post by ! ! ! winner on 2008-12-18
> **linux_tech said:**
> If you open your home folder in the file browser, how much free space is listed at the bottom?

[http://www.prizerebel.com/index.php?r=806574](http://www.prizerebel.com/index.php?r=806574)

---

### Post by bigbrovar on 2008-12-18
to know what is really taking ur hard drive. go to Applications/Accessories/Disk Usage Analyzer. 

then click on scan filesystem. it would give you a graphical out put on what is really eating your hard drive

u might also want to clear out your hard drive of packages installed via synaptics but cached on the system by doing ```
sudo apt-get clean 
```

---

