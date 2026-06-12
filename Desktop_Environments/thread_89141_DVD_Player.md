---
title: "DVD Player"
date: 2005-11-11
forum: Desktop Environments
---

### Post by cabpman on 2005-11-11
Hello All.

Thanks in advance for your assisstance.

I'm new to Linux.  I've read a bit but don't know much at all.  I'm excited to get started and have had some early success with learnng how to navagate.  Years ago I installed Red Hat.  It was nothing like this.  This is very exciting.

I'm finding it difficult to get my DVD support added to the system.  I'm following instructions that tell me to add lines to /etc/apt/sources.list file.  I was able to create the new file (since I can't modify the existing one since I am not the owner.)  I put the new file on my desktop and would like to replace the existing sources.list, then continue with the remaining instructions.  Please help.

Thanks

---

### Post by DJ_Max on 2005-11-11
If this is your computer, you have access to everything on it.

```
sudo gedit /etc/apt/sources.list
```

Enter your initial user accoun password to get proper privileges to edit that file.

---

### Post by Hairy_Palms on 2005-11-12
just download from
[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb)
then open a terminal and type 
sudo dpkg -i libdvdcss2_1.2.9-1_i386.deb and then your video players should be able to play DVDs

---

