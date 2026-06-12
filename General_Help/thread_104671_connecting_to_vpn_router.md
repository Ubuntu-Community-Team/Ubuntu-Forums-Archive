---
title: "connecting to vpn router"
date: 2005-12-16
forum: General Help
---

### Post by matva on 2005-12-16
hi
im currently using sshsentinel in windows to connect to my linksys vpn router

anyone know how i can do this in ubuntu? i'm a total newb, so something that lays it out step by step is preferred (thats the only way i managed sshsentinel).

---

### Post by scrillamaan on 2005-12-16
I have the same question. 
Btw, what model of linksys router do you have?

---

### Post by matva on 2005-12-16
i don't know off hand, but i'll check for you next time i'm at the office.

---

### Post by matva on 2005-12-16
i think i may have found a solution. download openswan
there is a gui for newbies like me called safeconnect ([http://www.secteta.com](http://www.secteta.com)). Looks similar to sshsentinel so i think it may work. haven't been able to try it cause i can't seem to compile it (requires qmake). Maybe someone can compile it for me? would appreciate it!

---

### Post by scrillamaan on 2005-12-18
[QUOTE=matva]i think i may have found a solution. download openswan
there is a gui for newbies like me called safeconnect ([http://www.secteta.com](http://www.secteta.com)). Looks similar to sshsentinel so i think it may work. haven't been able to try it cause i can't seem to compile it (requires qmake). Maybe someone can compile it for me? would appreciate it![/QUOTE]
This is definately something to look into. I don't have much time at the moment, (with the holidays and all) but next week I'm going to take a look at see if I can get it to work...heh or even compile. It seems we're both newbs, but that shouldn't stop us. I'll try to update this thread as time permits.

---

### Post by matva on 2005-12-19
don't bother with safeconnect... it doesn't work properly (at least not for me). 
do install openswan though.
then follow this tutorial: 
[http://www.freeswan.ca/docs/BEFVP41/](http://www.freeswan.ca/docs/BEFVP41/)

haven't got it to work yet, but i think that is only because i don't have the linksys settings matched. next time i go to the office i will match the settings and try. if i get it to work then i will most likely make a more detailed guide cause this one is kind of vague for a newb like me. let me know if you have any questions w/ it

---

