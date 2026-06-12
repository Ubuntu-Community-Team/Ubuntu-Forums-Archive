---
title: "Beryl doesn't work with enabled ATI accelerated graphics driver!"
date: 2007-05-30
forum: Desktop Effects &amp; Customization
---

### Post by Isoss on 2007-05-30
Hello. I have Ubuntu 7.04 with beryl installed which worked perfectly untill I decided to install some games that need 3d acceleration. So I enabled it and rebooted and beryl works no more! Even when I select window manager it doesn't change anything!

Is there any solution for that?

Thanks

---

### Post by blazercist on 2007-05-30
Ok for beryl to work with fglrx which is the ATI restricted driver you need to be using XGL not the AIGLX that ships with ubuntu...  For this i suggest you go to the beryl site and read about how to get ATI/XGL working on ubuntu.  Also, you cant run games with 3d acceleration during an XGL session, it will either run EXTREMELY slow or you will get all kind of graphical artifacts... so in order to play those games you will need to log out and chose a regular gnome session.

---

### Post by Isoss on 2007-05-30
Thanks. even though it isn't fun to do that all the time.

---

