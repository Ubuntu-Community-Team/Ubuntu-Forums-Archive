---
title: "Problems when installing..."
date: 2005-12-14
forum: General Help
---

### Post by cynic on 2005-12-14
When installing I get to where im suposed to create a new user. I type in my name, username and password and press ok. But it gets no furhter. It just jumps back to the same screen, but the fields are empty. 

If I cancle this step and proceed to the next, and finnish the instalation, there is no user which i can log on to.. 

Anybody know what the problem is? I have installed earlyer versions of ubuntu with no problem, but i cant figure this one out!

---

### Post by taurus on 2005-12-14
Which filesystem did you use?  Were you using ext2/ext3 for Linux or were you using vfat (or fat32)?

---

### Post by cynic on 2005-12-14
I use ext3 for my / partition and fat32 for my /home partition, so i can share it with windows..

---

### Post by RAOF on 2005-12-14
I'm pretty sure you can't use fat32 for anything critical to the functioning of Ubuntu.  This includes /home.  It just doesn't support the needed facilities (file permissions, links).

You could use a smallish ext3 /home partition for all the important user-settings and a fat32 partition mounted somewhere else to store all your actual data.

---

### Post by cynic on 2005-12-14
I worked! :) As you say I could'nt use Fat32 for my /home partition..! 

Thanks alot for the help! :)

---

