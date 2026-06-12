---
title: "Trouble reading a hard drive"
date: 2005-12-07
forum: General Help
---

### Post by soup440 on 2005-12-07
i have a hard drive partitioned for windows, calle /media/hda2
There is an Icon for it on my Ubuntu desktop and I am unable to access it, I says I do not have the permissions to access it. I looked in the permissions tab and it said that I couldn't change anything because I was not the owner. How do I fix this? 

Thanks!

---

### Post by aysiu on 2005-12-07
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by soup440 on 2005-12-07
Somehow I can't get this to work, but this is the first time I've used the terminal

---

### Post by aysiu on 2005-12-07
Is this an NTFS or FAT32 partition?

---

### Post by mherring on 2005-12-08
[QUOTE=soup440]Somehow I can't get this to work, but this is the first time I've used the terminal[/QUOTE]

could you be a bit more specific..........what happens?

I can mount my windows drive with:
     mount -t ntfs <device> <dir>
Does not seem to need the other stuff

you need to first create the destination directory, and to mount, you need to be "root"  (in principle "sudo" gets you that, but I don't like sudo---I like to be one or the other, like having two hats....;) )

---

