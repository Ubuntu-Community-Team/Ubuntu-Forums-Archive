---
title: "How to install this .deb program"
date: 2006-03-03
forum: Desktop Environments
---

### Post by tidy_boy on 2006-03-03
hey guys I have downloaded the lastest amsn amsn_0.95-3.ubuntu.deb

How do i install it please?


Thanks

---

### Post by tidy_boy on 2006-03-03
Ok I have figured out how to install it by using this

dpkg --install amsn_0.95-3.ubuntu.deb

but I get this error when I try to run it from a terminal 

Application initialization failed: no display name and no $DISPLAY environment variable

---

### Post by taurus on 2006-03-03
Are you running it as a regular user or as root?  Try running that program as a user...

---

### Post by aysiu on 2006-03-03
Go to Applications > Accessories > Terminal (not *root* terminal, just regular terminal) and type ```
cd Desktop
sudo dpkg -i amsn*.deb
``` This assumes, of course, that the .deb is on your desktop.

---

### Post by tidy_boy on 2006-03-03
When I run it as a normal user I get this error

Segmentation fault

And when I try to run it as root I get this message

Application initialization failed: no display name and no $DISPLAY environment variable


I am typing amsn to try to get it to open in a console :D

---

