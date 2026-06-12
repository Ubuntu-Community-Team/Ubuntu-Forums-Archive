---
title: "Permissions"
date: 2008-12-22
forum: General Help
---

### Post by burpootus on 2008-12-22
Hello, could someone tell me how to set permissions on a folder so that when I move a file into that folder, it will take on the folder's permissions? I have a shared folder on each of my two home computers, both running Linux. Whenever I want to copy a file from the other PC, I get permissions denied. I have to go to the other PC and chmod permissions on the folder. Then everything is ok until I move a new file into the folder. Then when I want to copy it over to the other PC, I am denied and I have to go chmod again. I want the folder and any of it's files to always have these permissions, if I move new files into the folder I want them to take on it's permissions by default. Can this be done? Thanks!

---

### Post by burpootus on 2008-12-22
bump

---

### Post by CatKiller on 2008-12-23
You can do that by setting the *setgid* flag on the parent directory. That will cause all new files and subdirectories to gain the groupID of the parent folder. If you set the group permissions appropriately, that should stop you getting any further problems.

---

