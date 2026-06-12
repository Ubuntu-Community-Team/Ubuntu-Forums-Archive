---
title: "conky retarded autostart"
date: 2009-08-20
forum: Desktop Environments
---

### Post by andres-bracho on 2009-08-20
Hi,

I installed and configured conky to start when I loging, but conky starts before wallpaper try, and when wallpaper try start sends conky to the background and then I can't see it... after some time I have to kill conky and start it again trough CLI...

How can I make conky autostart but being the last in the list or with a timer???

---

### Post by ajgreeny on 2009-08-20
You should probably try to work out why conky gets thrown to the background, but to wait for a number of seconds use the **sleep 10; conky** command instead of just **conky**.  You can use whatever delay you want.  It's a useful command option which can be very handy in a number of situations.

The default is for seconds, but you can also use **sleep 10m; conky** for minutes or **sleep 10h; conky** for hours if you want.

---

### Post by wotsit on 2009-08-20
this may help

[http://ubuntuforums.org/archive/index.php/t-386078.html](http://ubuntuforums.org/archive/index.php/t-386078.html)

---

### Post by wojox on 2009-08-20
Agreed, make a bash script that sleeps and calls conky. Remember to take the conky command out of the start up applications and add the bash script or you will end up with two instances of conky running.

---

