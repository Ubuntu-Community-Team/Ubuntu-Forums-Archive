---
title: "KDE 4 WIll Not Start"
date: 2008-05-04
forum: Desktop Environments
---

### Post by adrian007 on 2008-05-04
I installed KDE 4 (core) using synaptic. I logged out and went to sessions to select KDE 4 however i see the loading Hard disk thing. then the desktop displays briefly for 3 seconds and then i am back at the log in screen. are there any solutions to this



I am using Ubuntu 8.04



Thanks in advanced:):)

---

### Post by NightwishFan on 2008-05-04
Perhaps reinstall it if the situation is where the the install  somehow failed.
```
sudo aptitude update && sudo aptitude install kubuntu-kde4-desktop
```
If you just want kde4 you can use the package "kde4"

---

### Post by advoss on 2008-05-04
I have the same problem.  Reinstall did not help.  If its any use it also behaved the same way when i tried using the community packages (which i then removed) before it was put in the main repos.

---

### Post by adrian007 on 2008-05-05
No. i  i tried re-installing about 10 times. i used both kde4 core and kde4 (full desktop). 

I tried KDE 3 and that worked.

---

### Post by advoss on 2008-05-08
I updated to the new kde4 packages that i found in the repos this morning and it still doesn't work.

---

### Post by mutzinet on 2008-05-09
This sounds like the problem I encountered. 
I posted my solution here: [http://ubuntuforums.org/showthread.php?p=4847868#post4847868](http://ubuntuforums.org/showthread.php?p=4847868#post4847868)

---

### Post by advoss on 2008-05-10
Thanks for the reply mutzinet, however:
locate .ICEauthority returns:
/home/adam/.ICEauthority
/root/.ICEauthority

and ls -la /home/adam/.ICEauthority returns:
-rw------- 1 adam adam 191 2008-05-10 08:38 /home/adam/.ICEauthority

the one in root has the same permissions only belonging to root:root

Any other suggestions?

---

### Post by agent8131 on 2008-05-10
I've gotten this problem in 2 different virtual setups now in an attempt to test kde4: once starting with a  kde3 system and once starting with a server system.  Both experienced this same problem.  I'm currently reviewing my .xsession-errors file looking for the problem.

---

