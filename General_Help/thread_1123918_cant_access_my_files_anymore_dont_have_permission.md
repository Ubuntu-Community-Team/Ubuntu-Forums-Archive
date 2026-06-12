---
title: "cant access my files anymore dont have permission????"
date: 2009-04-12
forum: General Help
---

### Post by hairchin67 on 2009-04-12
still a novice and cant access my files anymore! dont know what i did. i was in the terminal before. everytime i try to open my music or video file browsers i get a message saying i dont have the necessary permissions to view its content. what did i do? how do fix this im frustrated!

---

### Post by javierd on 2009-04-12
Probably a windows session is still open, if so you cant use files present in windows hard drive

Just go back to windows and check, if system resumes just close it. A restart would be good enough

---

### Post by hairchin67 on 2009-04-12
i tried a restart still have the issue

---

### Post by Iowan on 2009-04-12
Try going to the directory via Places... Right-click the file and check Properties. Check Permissions to see who owns the file and the permissions.

---

### Post by banana jama on 2009-04-12
if you don't have permission for a file you can type:
```
sudo nautilus
```
right click on the file and go to permission and change the permission from root to you. if you don't have permission in that file partition you can also change the permission to you in the same way. hopes this helps.

---

### Post by hairchin67 on 2009-04-12
can anyone tell me what the orange sybol is that is over the files i cant open. it is a circle with a square inside it. it is preventing me from accessing my files. i tried the sudo natilus command via terminal but it says failed. i also noticed that my mouse icon keeps spinning whenever i go inside the blocked files .what is going on help

---

### Post by Iowan on 2009-04-12
Is that square a lock, or does it have an "X" on it? Lock is read-only, the X means no permissions. The right-click>Properties>Permissions would show as "No read, no write".

---

### Post by hairchin67 on 2009-04-12
thanx man fixed it

---

