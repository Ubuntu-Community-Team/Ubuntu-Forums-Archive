---
title: "Stuck at the login again."
date: 2006-07-12
forum: Desktop Environments
---

### Post by Brokenrgv on 2006-07-12
Im stuck at the login page using dapper, I enter user and pass both are correct, goes on to start the mouse clock shows then I end back at the login screen again, I can login to command line but not to either gnome or kde,please help

---

### Post by taavi on 2006-07-12
Can you login from console (found at Ctrl-Alt-F1)? Graphical login can be seen again by pressing Ctrl-Alt-F7.

---

### Post by Brokenrgv on 2006-07-12
can login to console but when back at graphical login im stuck at the login screen doesnt seem to get past that screen

---

### Post by taavi on 2006-07-12
Isn't it possible that your partition for Ubuntu is full? I have experienced problems with login when partition for / was full.

Login from console and do 'df -h' from there. It shows you how full your disks are.

---

### Post by Brokenrgv on 2006-07-12
df-h doesnt work but df does, yes hda1 is 100% whats the delete comand from console by anychance? thanks for the tip btw hopefully thats the prob

---

### Post by taavi on 2006-07-12
The command was df<space>-h. '-h' is key for df for human readable size.

rm is the command to delete files.

You can also run command 'sudo apt-get clean' to clean downloaded .deb packages which can re-downloaded any time. 

How big is your root partition by the way?

---

### Post by Brokenrgv on 2006-07-12
sorry missed the space, its mounted on a 80 gig drive, im trying to delete stuff via console on my desktop but keep hitting "Is a directory" when trying to rm stuff how do you delete directories? cant seem to free up even 1% to test if this is even the prob

well there you go managed to delete some vids that were big enough to free a decent amount of space and what do you know I can boot back into kde, thank you so much I had the cd's at the ready for yet another re install so you have saved me a heap of trouble, thanks again taavi :)

---

### Post by computx on 2006-07-12
If you want to delete a directory use rm -r  (-r for recursion). If the directories have subdirectories then you may need to use rm -rf (-f to force). 

BE CAREFUL! rm -rf can be a dangerous command if used with the wrong directory name.

---

### Post by mcduck on 2006-07-12
you might also want to run 'sudo apt-get clean' to remove all cached package files.. That should free you some disk space easily :)

---

### Post by Brokenrgv on 2006-07-12
thanks for all the help on this ppl, ive since logged in to kde and moved a heap of files onto another disc to free up some space so i dont hit this problem again, thanks again for the fast help saved me a re install

---

