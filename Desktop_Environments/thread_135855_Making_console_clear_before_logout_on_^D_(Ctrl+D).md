---
title: "Making console clear before logout on ^D (Ctrl+D)"
date: 2006-02-24
forum: Desktop Environments
---

### Post by jchau on 2006-02-24
Since I disabled GDM, I've been using the text consoles more often.  However, I noticed that whenever I logout, whatever I leave on the screen remains there.  I want to clear my screen before logging out because I have two roommates (I live in a dorm) and they often leave the door unlocked, so many people enter my room & I don't want them to see what I'm doing.  

I normally logout with [Ctrl]+[D]. I know that I can type:
```
clear && logout
``` in order to leave nothing behind, but I often forget to do this and press ^D instinctively to logout.  The I have to login again (which is a tedious process for me since my password is quite long).  

I know I can set an alias for logout:
```
alias logout="clear && logout"
```, but this doen't seem to make ^D clear and logout.  

Is there a way to make [Ctrl]+[D] clear the terminal or make the terminal automatically clear on logout?

Thanks.

---

### Post by angkor on 2006-02-24
don't know how to do it automatically but can't you just type:

Ctrl-L
Ctrl-D

---

### Post by jchau on 2006-02-24
[QUOTE=angkor]don't know how to do it automatically but can't you just type:

Ctrl-L
Ctrl-D[/QUOTE]
Thanks. Didn't know about the Ctrl+L & I think that with enough practice, I can remember to press ^L.  It is convenient, but it still leaves the last command prompt.  It isn't much, and your solution should do for me, but it still nags me.  

If it executes all in the same line, like clear && logout, nothing is left behind. 

Thanks though, but I'm still open to further suggestions.

---

### Post by lamego on 2006-02-24
I didn't test it but it should work according to the man pages:

>        When a login shell exits, bash reads and  executes  commands  from  the
       file ~/.bash_logout, if it exists.

---

### Post by jchau on 2006-02-24
[QUOTE=lamego]I didn't test it but it should work according to the man pages:[/QUOTE]


Thanks:-D Works beautifully!

---

