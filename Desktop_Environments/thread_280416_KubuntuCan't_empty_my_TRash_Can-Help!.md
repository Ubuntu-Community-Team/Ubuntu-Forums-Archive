---
title: "Kubuntu:Can't empty my TRash Can-Help!"
date: 2006-10-19
forum: Desktop Environments
---

### Post by mibadt on 2006-10-19
Hi,
While video editing on my (fully updated) Kubuntu dapper, I erred and targeted an output mpeg (large) file to my home directory.
I exited to video edit program, located the large file, and initially tried to cut it (Ctrl-X). After a few seconds I lost my patience and dragged the same file to the Trash.

That's where I'm stuck, **even after a reboot**:
1. The file does not show up any more in my home folder.
2. df -h shows still 100% usage for my home
3. When I try to empty the Trash can, I get the following error: "could not read /home/usr/.local/share/Trash/info/mpeg_file_name.trashinfo"
4.I've checked there and there is such a file, **with 0 zise (=zero !)** and user read permission.


Please advise how to regain my space.

Thanks in advance !
;)

---

### Post by hopstah on 2006-10-20
delete everything in the subfolders under your /home/'username'/.local/share/Trash folder using the command line and a sudo command.  i had this problem recently as well, and doing a ```
sudo rm /home/'username'/.local/share/Trash/info/*
sudo rm /home/'username'/.local/share/Trash/files/*
```did the trick

---

### Post by mibadt on 2006-10-20
Thanks a lot !
You've made my day ! - I've r**egained 3.4 G** !

:D 
Take care

Michael Badt

---

### Post by hopstah on 2006-10-23
glad i could help :)

---

