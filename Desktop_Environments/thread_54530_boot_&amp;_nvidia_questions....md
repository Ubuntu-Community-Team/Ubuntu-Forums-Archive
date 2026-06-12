---
title: "boot &amp; nvidia questions..."
date: 2005-08-05
forum: Desktop Environments
---

### Post by obx-jdt on 2005-08-05
Untill about a month ago I was running Mandrake 10.1 
I really like this Ubuntu but one thing is driving me crazy. With Mandrake I could boot directly into the command line without the x-server starting. I found this quite usefull for installing all sorts of stuff (like the Nvidia driver) and system utilities. When I was ready for a GUI all I had to do was type "startx". For the life of me, I can't seem to figure out how to get Ubuntu to boot into the command line....
 This brings me to the second part of my question....How do I install the latest Nvidia driver if I can't boot into the command line? I know I can kill x with "/etc/init.d/gdm stop" but I want to be able to log in and out of x like I can on a redhat based system. 
Hehe. took me a few to realize that "startgdm" was the command for Ubuntu, not "startx" LOL
With startx the user is still logged in with startgdm, you have to re-login.


*EDIT* 
Yeah I know if I want readhat commands to work I can go back to Mandrake but I really like Ubuntu. Not being able to boot into the command line is my only real complaint so far.

---

### Post by defkewl on 2005-08-05
1. Open up /etc/inittab
2. FInd these line: id:2:initdefault:
3. Change the number to the ones that suits you

---

### Post by obx-jdt on 2005-08-05
I'll look into it now. I assum there is a value code there that explains what number is for what  :???: 
I'll post back later with my results.....
Thanx for the info  ;-)

---

