---
title: "Just a few simple questions"
date: 2009-01-03
forum: General Help
---

### Post by sofasurfer on 2009-01-03
Just a few simple questions...
1. What is /lost+found for?
2. What is vmlinux?
3. Why, when I go to places>computer and I click on one drive icon, I can see a pie chart which instantly shows disk space, but when I click on another icon I do not get a pie chart but I have to wait a couple of minutes to watch the size be calculated?
4. Why does a directory's size not reflect the size of all the directories inside of it? Doesn't this make its reported size irrelavant?
5. Is there a button to automaticaaly empty /root/.local/share/Trash? How many people even know its there taking up space?

---

### Post by cariboo on 2009-01-03
> 1. What is /lost+found for?

Lost+found is where fsck places recoverd files after a hard drive crash. It is OK to remove the directory, as fsck will add the directory when needed.

> 2. What is vmlinux?

from Wikipedia > On Linux systems, vmlinux is a statically linked executable file that contains the Linux kernel in one of the executable file formats supported by Linux, including ELF, COFF and a.out. The vmlinux file might be required for kernel debugging, generating symbol table or other operations, but must be made bootable before being used as an operating system kernel by adding a multiboot header, bootsector and setup routines.

> 3. Why, when I go to places>computer and I click on one drive icon, I can see a pie chart which instantly shows disk space, but when I click on another icon I do not get a pie chart but I have to wait a couple of minutes to watch the size be calculated?

I'm running jaunty and I don't have a Places-->Computer, but when I have other disks mounted I get the pie chart right away, but it is still calculating the size.

> 4. Why does a directory's size not reflect the size of all the directories inside of it? Doesn't this make its reported size irrelavant?

I find a lot of the gui tools irrelevant, I just open a terminal and type:

```
du -h
```

the above command means disk usage in human readable form

> 5. Is there a button to automaticaaly empty /root/.local/share/Trash? How many people even know its there taking up space? 

You shouldn't need a button, as you shouldn't be moving files to trash as root, go to Places-->Home Folder-->Edit-->Preferences-->Behavior and enable Include a Delete command that bypasses Trash. Then if you have to delete a file as root, delete it instead of sending it to trash. If you are trying to delete files as root you surely are not going to restore them.

Jim

---

### Post by sofasurfer on 2009-01-03
Thanks for some good answers. The du command is GREAT!!
I am slowely getting it through my head to be more careful as root. That is the root of many of my problems, pun intended. Sometimes, for instance when restoring my systen I will be root to restore my sources.lst and than I continue as root to restore /home items. This cause all of my permissions to need resetting. Stuff like that is a bad habit. Sometimes its confusing as to when to use sudo.

---

