---
title: "Major Number"
date: 2009-02-18
forum: General Help
---

### Post by Lekshmi on 2009-02-18
How we will find the major number and minor number?
i have to create a char device using mknod?

---

### Post by halovivek on 2009-02-18
Could you please reply with more details?

---

### Post by Lekshmi on 2009-02-18
am writting a sample driver program. so for my module to run, i have to create a chardevice file.
like...mknod /dev/hello c 60 0
where hello is the module. i dont know which all major numbers are occupied...

---

### Post by heindsight on 2009-02-18
Look at Documentation/devices.txt in the kernel source (although that may be a bit outdated). It would probably also be a good idea to look at Documentation/SubmittingDrivers.

Also have a look around [www.lanana.org](www.lanana.org) particularly [http://www.lanana.org/docs/device-list/index.html](http://www.lanana.org/docs/device-list/index.html)

EDIT:
Also keep in mind that linux no longer uses a static /dev but rather a dynamic /dev managed by udev.

---

### Post by halovivek on 2009-02-18
i hope this [link]("www.freesoftwaremagazine.com/articles/drivers_linux") will help you.

---

