---
title: "broken sudo after updating"
date: 2009-02-20
forum: General Help
---

### Post by lammergeir on 2009-02-20
Hi grateful for guidance. 
I updated software on Tuesday, then sudo stopped working.  Couldn't open synaptic. 
Error message then was:
sudo: /etc/sudoers is owned by gid 1002, should be 0  
Tried to follow advice in [http://ubuntuforums.org/showthread.php?t=943614&page=2](http://ubuntuforums.org/showthread.php?t=943614&page=2) 
Obviously messed it up very well. Now the error is:

terry@lammergeir:~$ sudo
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
>>> sudoers file: syntax error, line 10 <<<
>>> sudoers file: syntax error, line 11 <<<
>>> sudoers file: syntax error, line 12 <<<
>>> sudoers file: syntax error, line 13 <<<
>>> sudoers file: syntax error, line 14 <<<
>>> sudoers file: syntax error, line 15 <<<
>>> sudoers file: syntax error, line 16 <<<
>>> sudoers file: syntax error, line 17 <<<
>>> sudoers file: syntax error, line 18 <<<
>>> sudoers file: syntax error, line 19 <<<
>>> sudoers file: syntax error, line 20 <<<
>>> sudoers file: syntax error, line 21 <<<
>>> sudoers file: syntax error, line 22 <<<
>>> sudoers file: syntax error, line 23 <<<
>>> sudoers file: syntax error, line 24 <<<
>>> sudoers file: syntax error, line 25 <<<
>>> sudoers file: syntax error, line 26 <<<
>>> sudoers file: syntax error, line 27 <<<
>>> sudoers file: syntax error, line 28 <<<
>>> sudoers file: syntax error, line 29 <<<
>>> sudoers file: syntax error, line 30 <<<
>>> sudoers file: syntax error, line 31 <<<
>>> sudoers file: syntax error, line 32 <<<
>>> sudoers file: syntax error, line 33 <<<
>>> sudoers file: syntax error, line 34 <<<
>>> sudoers file: syntax error, line 35 <<<
>>> sudoers file: syntax error, line 36 <<<
>>> sudoers file: syntax error, line 37 <<<
>>> sudoers file: syntax error, line 38 <<<
>>> sudoers file: syntax error, line 39 <<<
>>> sudoers file: syntax error, line 40 <<<
>>> sudoers file: syntax error, line 41 <<<
>>> sudoers file: syntax error, line 42 <<<
>>> sudoers file: syntax error, line 43 <<<
>>> sudoers file: syntax error, line 44 <<<
>>> sudoers file: syntax error, line 45 <<<
>>> sudoers file: syntax error, line 46 <<<
>>> sudoers file: syntax error, line 47 <<<
>>> sudoers file: syntax error, line 48 <<<
>>> sudoers file: syntax error, line 49 <<<
>>> sudoers file: syntax error, line 50 <<<
>>> sudoers file: syntax error, line 51 <<<
>>> sudoers file: syntax error, line 52 <<<
>>> sudoers file: syntax error, line 53 <<<
>>> sudoers file: syntax error, line 54 <<<
>>> sudoers file: syntax error, line 55 <<<
>>> sudoers file: syntax error, line 56 <<<
>>> sudoers file: syntax error, line 57 <<<
>>> sudoers file: syntax error, line 58 <<<
>>> sudoers file: syntax error, line 59 <<<
>>> sudoers file: syntax error, line 60 <<<
>>> sudoers file: syntax error, line 61 <<<
>>> sudoers file: syntax error, line 62 <<<
>>> sudoers file: syntax error, line 63 <<<
>>> sudoers file: syntax error, line 64 <<<
>>> sudoers file: syntax error, line 65 <<<
>>> sudoers file: syntax error, line 66 <<<
>>> sudoers file: syntax error, line 67 <<<
>>> sudoers file: syntax error, line 68 <<<
>>> sudoers file: syntax error, line 69 <<<
>>> sudoers file: syntax error, line 70 <<<
sudo: parse error in /etc/sudoers near line 0


Programme apps are working. Please help, someone!!

---

### Post by Nepherte on 2009-02-20
Boot into recovery mode and open /etc/sudoers with the visudo command:
```
visudo
```
visudo uses vi, but if you prefer another editor, you can do something like:
```
EDITOR=nano visudo 
```
You can replace nano with the editor you like.

---

### Post by taurus on 2009-02-20
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by ljoslin on 2009-02-20
I'm currently having the same problem.  I had the same problem when I first install intrepid, but for the life of me I can't remember what the solution was.

-=Ljoslin=-

EDIT : Nevermind I got it

boot into recovery mode

chgrp 0 /ete/sudoers

---

### Post by lammergeir on 2009-02-23
Hi, I've tried the solution offered in Fix broken sudo.
I typed the first line sudo cp ......backup, hit enter and all it gives is the list of syntax errors and parse error I posted above.

Also tried chgrp 0/etc/sudoers and was told something's missing.  I'm a noob at coding not sure what next to do.
Visudo won't function either. Thanks for suggestions.

---

### Post by dusenn on 2009-10-01
Hi, i have almost the same issue, i upgraded to jaunty jackalope few days ago and now every time that i try to install or update an application i get this: "/etc/sudoers is owned by gid 1002, should be 0"... 
the thing is that i already check if the user was included to de administrator group, and it is... so now i dont what to do next...

---

### Post by dusenn on 2009-10-01
Hi, i have almost the same issue, i upgraded to jaunty jackalope few days ago and now every time that i try to install or update an application i get this: "/etc/sudoers is owned by gid 1002, should be 0"... 
the thing is that i already check if the user was included to de administrator group, and it is... so now i dont what to do next...

---

