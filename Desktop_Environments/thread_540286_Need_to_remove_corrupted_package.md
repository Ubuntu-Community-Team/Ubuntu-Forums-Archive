---
title: "Need to remove corrupted package"
date: 2007-09-01
forum: Desktop Environments
---

### Post by rkakkar on 2007-09-01
The installation of a package got aborted abruptly. Now I can't enter Synaptic to remove it. I get the following error (see screenshot). How can I fix this?

---

### Post by tropcky on 2007-09-01
oky bro i am new as hell but i had thes prop befor
look 
open the synaptic pakages manager  and  open the felter and mark on broken   so u will se the broken packages remove them 
i hop if i helped 
good luck

---

### Post by rkakkar on 2007-09-01
I would have done that if I can get into Synaptic! :-D. The second I click the "close" button on the message box, Syaptic exits!! I even tried running "sudo apt-get remove smc" from the terminal and it throws the same error message and returns to prompt!

---

### Post by tropcky on 2007-09-01
oky budy tray 2 change or upgrade ur sources list   



ons agen i am new

---

### Post by tropcky on 2007-09-01
and yes   tray to post that into comand line 
sudo dpkg --configure -a 
try it maby will help it helps me with some broken programs its
sudo dpkg --configure -a 
or 
sudo dpkg --configure-a

---

### Post by rkakkar on 2007-09-01
nope. still broken. :-(

---

### Post by tropcky on 2007-09-01
oooooooooh i am sorry man i really want to help but i dont how some body gonna see thes and gonna help i am sure 
hop u luck

---

### Post by rkakkar on 2007-09-01
anyone?!

*bump*

---

### Post by jmedema on 2007-09-06
Before I attempt to help, let me make a few notes:
1) I'm new to Ubuntu/Debian, so anything I say may be totally off-base
2) My situation is probably slightly different from yours.  I got the same error on a different corrupted package, and I wanted to remove it (without re-install).  

This will help you simply remove the corrupt package.  Whether it will re-install again is up to you and your skills...

1) cd /var/lib/dpkg
2) sudo cp available available.bad
3) sudo cp status status.bad
4a) open available with a text editor.
4b) remove all references to offending package.  Save/close.
5a) open status with a text editor.
5b) remove all references to offending package.  Save/close.
6) cd info
7) delete all files relating to package.  

This cleaned out the debian package DB for me.  You might need to repeat step 7 for other dpkg subdirectories...

---

### Post by Lazlo Woodbine on 2007-12-23
jmedema,

Thank you so much! This work perfectly for a badly corrupted package that I had.

---

### Post by jmedema on 2007-12-24
Glad to help.  Now help someone else, as a Christmas present to me...

---

### Post by boterbram on 2008-01-23
> **jmedema said:**
> Before I attempt to help, let me make a few notes:
1) I'm new to Ubuntu/Debian, so anything I say may be totally off-base
2) My situation is probably slightly different from yours.  I got the same error on a different corrupted package, and I wanted to remove it (without re-install).  

This will help you simply remove the corrupt package.  Whether it will re-install again is up to you and your skills...

1) cd /var/lib/dpkg
2) sudo cp available available.bad
3) sudo cp status status.bad
4a) open available with a text editor.
4b) remove all references to offending package.  Save/close.
5a) open status with a text editor.
5b) remove all references to offending package.  Save/close.
6) cd info
7) delete all files relating to package.  

This cleaned out the debian package DB for me.  You might need to repeat step 7 for other dpkg subdirectories...


Thanks a lot, it worked for me too, I almost reinstalled xubuntu, thanks

---

