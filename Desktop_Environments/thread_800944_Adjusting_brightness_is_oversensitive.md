---
title: "Adjusting brightness is oversensitive"
date: 2008-05-20
forum: Desktop Environments
---

### Post by eOgas on 2008-05-20
I'm running Hardy on a Dell Inspiron e1705 and the Fn-arrow key assignment for brightness still works, somewhat.  See, in Gutsy it worked fine as anyone would expect, but for some reason in Hardy it seems to only be able to increase or decrease the brightness by a factor of 6.  Since there are only 10 brightness levels, you can see why this is a problem.  I can only get it to set to levels 0, 4, 6, and 10.  Does anyone know how to fix this?  Any help would be greatly appreciated.

EDIT: Whoops, sorry, doesn't really look like this is the right section.  Would an admin please move this to an appropriate board?

---

### Post by maxdamage2122 on 2008-05-20
same problem here on my dell inspirion 1700 running hardy.  im searching for a solution and if i find one i will post it.

EDIT:
this worked for me
Add "blacklist video" in /etc/modprobe.d/blacklist
Then restart.

found it in this thread [http://ubuntuforums.org/showthread.php?t=767219&highlight=brightness]("http://ubuntuforums.org/showthread.php?t=767219&highlight=brightness")

---

### Post by eOgas on 2008-05-20
Awesome.  Thank's man, that worked perfectly.  I didn't even get the problem like most people where the brightness doesn't automatically change when you remove/plug in the power cable.  Thanks has been given!

---

