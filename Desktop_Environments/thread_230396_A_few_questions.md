---
title: "A few questions"
date: 2006-08-05
forum: Desktop Environments
---

### Post by Szurgot on 2006-08-05
ok i have 2 problems

Problem 1. the most annoying 

I would like to install Gdesklets. I have downloaded the file on there site and have found no installer or instructions at all. help would be great.

problem 2.

I'm trying to install 3ddesktop and when ever i get it started i get this error  

Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

well after some serching of the fourm i found that was due to me not installing my video cards drivers. so i went and got them from ATI.com well when i click on the installer it dosen't do anything at all. no open windows no nothing. i also tried to open it in terminal and nothing happened then either.

---

### Post by Jagot on 2006-08-05
For gdesklets you need to enable the universe repository, then from Terminal:

```
sudo aptitude update
sudo aptitude install gdesklets
```

I have no idea about the 3ddesktop issue.

---

### Post by Szurgot on 2006-08-05
ok i ran what you told me to do it said everything setup correctly . now should i restart the computer or  should it have shown up immeditly?

also thanks for the help and  dose anyone have any idea about the 3dsek problem??

---

### Post by Jagot on 2006-08-05
It should be in one of the menus.  If not then restart the comp.

---

### Post by Szurgot on 2006-08-05
ok i got it to work thanks for all the help. now i was wondering is there a way to have the desklets  only appear on one of the workspaces not all of them??

---

