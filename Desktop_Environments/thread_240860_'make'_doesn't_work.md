---
title: "'make' doesn't work"
date: 2006-08-21
forum: Desktop Environments
---

### Post by pwrstick on 2006-08-21
Hello,

Trying to compile a driver, and am asked to run "make".  I  know this should do something, but I get :

bash: make: command not found

What do I need to apt-get to make that go?
Thanks
-Phil

---

### Post by kimara on 2006-08-21
apt-get install make

---

### Post by avtolle on 2006-08-21
Or, sudo apt-get install build-essential, to get all the needed "stuff" installed.

---

### Post by aysiu on 2006-08-21
Or ```
sudo aptitude update
sudo aptitude install build-essential
``` [It's good to get in the habit of using *aptitude* instead of *apt-get*](http://www.psychocats.net/ubuntu/aptitude)

---

