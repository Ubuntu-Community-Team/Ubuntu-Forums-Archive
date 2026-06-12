---
title: "AMD CPU driver necessary?"
date: 2006-08-13
forum: Desktop Environments
---

### Post by WalmartSniperLX on 2006-08-13
Hey I was wondering if its necessary to install an AMD driver for the 32bit version of ubuntu. thanks

---

### Post by kerry_s on 2006-08-13
no, but you can use "athcool" to keep it running cooler. Mine runs 10% cooler with it, it use to always be in the 50's tmp but now it runs around 35-40. It's easy to install and use in command line> sudo apt-get install athcool < then add> sudo athcool on <to the startup program. Then add to the /etc/sudoers> athcool ALL=NOPASSWD: ALL <as root, you also got to change sudoers to be writeable and change it back after your done(right click properties>permissions.)

---

### Post by az on 2006-08-13
Not a driver, but a differnet kernel.  Instal linux-k7 and you may notice some performance gains.

search for "linux-k7" in your favorite package manager and install it.  Reboot into your new kernel.

---

### Post by WalmartSniperLX on 2006-08-13
Ok thanks :D

---

