---
title: "X is not working"
date: 2007-09-14
forum: Desktop Environments
---

### Post by eduardo_atx on 2007-09-14
hello friends

when i run the command "startx x" i get the next error:

  xauth: creating new authority file /home/eduardo/.serverauth

xauth: error in locking authority file

xauth: error in locking authority file

xauth: error in locking authority file

xauth: error in locking authority file


and after a while....


/etc/X11/X is not executable

giving up

xinit: connection refused (errno 111): unable to connect to x server

xinit: No such process (error 3): server error.

xauth: error in locking authority file /home/eduardo/.Xauthority


I use ubuntu 7.04. was using beryl and everything was good. then i installed compiz fusion and waned to get back to berly son i uninstalled compiz and the next time i tried to run X i couldn't.

i need your help

thanks.

---

### Post by por100pre1 on 2007-09-14
Try this:

```
sudo chmod -R 755 /home/eduardo
```
```
sudo chown -R eduardo /home/eduardo
```

Hope it helps. :)

---

