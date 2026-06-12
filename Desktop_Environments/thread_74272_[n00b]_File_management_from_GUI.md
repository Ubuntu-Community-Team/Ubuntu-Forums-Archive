---
title: "[n00b] File management from GUI?"
date: 2005-10-11
forum: Desktop Environments
---

### Post by James_Nostack on 2005-10-11
I am pretty new to Linux.  I would like to move certain files from my **/home** folder to, say, the **/usr** directory.  Is there any way to do this from the GUI?  When I go to File Browser, for example, **/usr** is locked.  Since I'm the root user of this computer, having it tell me I can't do this is a little frustrating.

I know how to do this using the terminal, but I would prefer to use the GUI if possible.

thank you for your time!

---

### Post by kosmic on 2005-10-11
[quote=James_Nostack]I am pretty new to Linux. I would like to move certain files from my **/home** folder to, say, the **/usr** directory. Is there any way to do this from the GUI? When I go to File Browser, for example, **/usr** is locked. Since I'm the root user of this computer, having it tell me I can't do this is a little frustrating.
 
I know how to do this using the terminal, but I would prefer to use the GUI if possible.
 
thank you for your time![/quote]
 
 
Ok just open a terminal and write the following :
 
gksudo nautilus, and after a few seconds nautilus will ask you for your password type it and nautilus opens as root

---

### Post by az on 2005-10-11
In a sense, there is no reason why you would need to put something in /usr.   

Now, if you want to just have a seperate partition to store stuff, just mount it and make it world-read/writeable.

You could do the same by just creating a folder somewhere (maybe in /home)

ex:
/home/me
/home/mywife
/home/shared

---

