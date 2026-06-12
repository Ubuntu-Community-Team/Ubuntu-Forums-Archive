---
title: "[SOLVED] 8.04 a qucik question about find"
date: 2008-12-03
forum: General Help
---

### Post by guiliker on 2008-12-03
Every now and again when my partition is claiming to be full I run a check to see what big files I've got. I use the command ```
sudo find / -size +500M
``` amongst the results I got this and I don't understand it! ```
find: /proc/12600/task/12600/fd/4: No such file or directory
find: /proc/12600/task/12600/fdinfo/4: No such file or directory
find: /proc/12600/fd/4: No such file or directory
find: /proc/12600/fdinfo/4: No such file or directory
```

AFAIK proc is something virtual to do with system processes and doesn't take up any physical memory space but I've not been able to find anything google wise about this result....thanks for any advice please?

---

### Post by albandy on 2008-12-03
/proc is a filesystem that works as an interface to kernel data structures.

Find shows the message "No such file or directory" because the file descriptor "4" was deleted (automatically) while the find command was running, 12600 is the pid of a running process.

---

### Post by guiliker on 2008-12-03
The thing that was bugging me was that i couldn't find a process related to 12600 however your reply got me thinking. I ran "top" from one terminal whilst running "find" from another terminal and watched as the I got the same find result but the PID referred to "find".

Thanks for the inspiration albandy :-)

---

### Post by geirha on 2008-12-03
If you add the -xdev option, find will only look in one filesystem and skip any other filesystem that may be mounted in its path. That also means that if /home is on a seperate partition and you instruct find to start searching on /, then /home will not be searched.

```
sudo find / -xdev -size +500M
```

---

