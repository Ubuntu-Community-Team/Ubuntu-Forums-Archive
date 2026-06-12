---
title: "About navigation with Wine"
date: 2011-10-14
forum: Desktop Environments
---

### Post by Leo_N on 2011-10-14
Hi,
I have a problem to install a program with Wine, I searched why and I found that I have to change a file in :
C:\USER\AppData\....
But folders and files in AppData folder are hidden, I tried to find a solution in many forums but i did'nt find. So I ask the question now:

How can I "unhide" folders in wine?
I tried Ctrl+ H , it does'nt works,
 I tried also to put this lines at the end of file : 
root/USER/user.reg 

"
[Software\\Wine\\X11 Driver] 1226210902
"ClientSideWithRender"="N"
"
it does'nt work

Someone knows?

---

### Post by fritz269 on 2011-10-15
you should be able to navigate to a folder and in the menu bar there is an option to show hidden files

---

