---
title: "Partimage problem"
date: 2005-07-05
forum: Desktop Environments
---

### Post by manicka on 2005-07-05
I installed Partimage to use for backups of my system.

At start up 'sudo partimage' ,  I get the screen below. Selecting Yes does nothing, it just stays stuck at this point.

Any ideas?
[IMG]http://img272.imageshack.us/img272/3921/partimage0ot.png[/IMG]

---

### Post by jeremy on 2005-07-06
I think you need to run as root, set a root password: sudo passwd root
then run the console as root.

I use partimage a lot, but run it from a knoppix cd.

---

### Post by manicka on 2005-07-06
Thanks, 
I'll give the knoppix idea a go

---

### Post by jeremy on 2005-07-07
In knoppix do not mount the partition that you are imaging, but you must mount the partition that you are writing the image to, and make it writable.

---

### Post by manicka on 2005-07-07
ok great :D , thanks again

---

