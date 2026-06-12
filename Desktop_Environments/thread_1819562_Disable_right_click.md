---
title: "Disable right click"
date: 2011-08-06
forum: Desktop Environments
---

### Post by sakthi.pace on 2011-08-06
Is there any option to disable mouse right click on ubuntu 11.04 in Gnome.

---

### Post by realzippy on 2011-08-06
Welcome.
May I ask why you want this ?
Maybe there is a smarter solution...

---

### Post by realzippy on 2011-08-06
anyway,here is a hack:
[http://ubuntuforums.org/showthread.php?t=1176963](http://ubuntuforums.org/showthread.php?t=1176963)

---

### Post by sakthi.pace on 2011-08-06
Need to customize my desktop. I tried but no luck

---

### Post by realzippy on 2011-08-06
Booted my 11.04 for you (formerly tested on 10.10)

```
xmodmap -e "pointer = 1 2 99"
```

works in 11.04 also.
????

---

### Post by enimeizoo on 2011-08-06
You can still unmap it with xmodmap. But it would be system-wide, so you won't have it in softwares either. You could bind a shortcut to activate/deactivate it, though.
Just so you know, the command is :
```
xmodmap -e 'pointer = 1 2 0 4 5 6 7 8 9'
```If you want to reverse it, 
```
xmodmap -e 'pointer = default'
```Not sure it helps, just some ideas.
Good luck.

(edit) I didn't see your post, but yes, right-click is button 3 (not 2 as I thought). That said, the 0 is here to unmap. The difference being that it wont send an event, instead of sending button 99.

---

### Post by sakthi.pace on 2011-08-09
Thanks realzippy  and enimeizoo
 
its worked =D>

---

### Post by realzippy on 2011-08-09
Fine...so set thread as solved please..(threadtools)
Have fun!

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

