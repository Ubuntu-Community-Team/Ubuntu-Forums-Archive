---
title: "ubuntu partition resize"
date: 2005-12-27
forum: General Help
---

### Post by noeluylee on 2005-12-27
I have 80gb of hard disk space. currently here's the partition
20gb = ext3 /
20gb = ext3 /home
20gb = fat32 /data
20gb = ntfs = windowsxp

I am planning to take some 10gb space from windows xp using partition magic, and i want to add it to ext3 / and maybe some 5gb from /home to /   but I dont know how to add it to linux partition.

Is there any partition magic like application for linux or any command line for linux. 

Hope you guys can suggest me what to do. 

Thanks a lot :)

Noel

---

### Post by ubuntu27 on 2005-12-27
You can use gparted, but, make sure that you backup your files.
One never know what could happen ;)

---

### Post by stuporglue on 2005-12-27
If there's just one place you need the space, it's easiest to just make a new partition out of that free space and mount it somewhere. For example, if you need it for music, just mount it in your home folder as /home/username/music. 

That way you avoid the resizing issues entirely, and have less risk of data loss.

---

### Post by noeluylee on 2005-12-27
Hi, Thanks I just installed gparted, its kool! :) thanks. I still have lots of space, but I just want to know for future reference :) sorry but just learning linux. :) 

Thanks a lot. :)

---

### Post by ubuntu27 on 2005-12-27
You're welcome noeluylee :)

---

