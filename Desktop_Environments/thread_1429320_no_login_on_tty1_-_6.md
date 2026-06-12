---
title: "no login on tty1 - 6"
date: 2010-03-13
forum: Desktop Environments
---

### Post by oneindelijk on 2010-03-13
Hi, 

For a while, I've noticed that I have no possibility to login in the commandline consoles tty1 to tty6.
This is similar to this thread
[HTML]http://ubuntuforums.org/archive/index.php/t-1359809.html[/HTML]
with the difference that the consoles seem to be running.
When I execute 
```
who -all
```
```
sam      + tty7         2010-03-12 11:31  old         1127 (:0)
           pts/0        2010-03-13 14:37             24310 id=/0    term=0 exit=0
           tty1         2010-03-12 21:58              7487 id=:1    term=0 exit=0
sam      + pts/1        2010-03-13 14:38   .         24521 (:0:S.0)
           pts/2        2010-03-13 14:41             25723 id=p2    term=0 exit=2
           pts/3        2010-03-13 14:41             25536 id=p3    term=0 exit=2
           pts/4        2010-03-13 14:41             25711 id=p4    term=0 exit=2
           pts/5        2010-03-13 14:41             25759 id=p5    term=0 exit=2
           pts/6        2010-03-13 14:40             25765 id=p6    term=0 exit=2
marsita  + tty2         2010-03-13 20:36  old        21185 (:2)
```
It seems also an anomality to me that on tty1 the login screen is running and when a second user logs in through the grafical console (using the switch user option), X is running on tty2 instead of tty8, 9 or 10 as I'm used to.
Any ideas ?

---

### Post by oneindelijk on 2010-03-29
No, When I log in the graphical session runs on TTY3 ?
But I'm about to reinstall my pc, so proabably al problems will be solved ;-)

---

### Post by oneindelijk on 2010-04-14
Reinstalled - Solved

---

