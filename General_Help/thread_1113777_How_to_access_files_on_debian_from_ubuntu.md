---
title: "How to access files on debian from ubuntu"
date: 2009-04-02
forum: General Help
---

### Post by texas.chef94 on 2009-04-02
I know it has been answered before, I looked and did not find so if I am booted to Ubuntu and I have Debian as well how do I access files on Debian 
Do not know if it is relevant but I am in a triple boot with 3 Linux OS
Please advise and thanks

---

### Post by sekinto on 2009-04-02
You can check your /media directory to see if Ubuntu automatically mounted it. If Ubuntu isn't automatically mounting it you can always add its filesystem to your /etc/fstab file.

---

### Post by adult swim on 2009-04-02
or you can run ```
sudo mount /dev/sdaX /mnt
``` changing sdaX to whatever the debian partition is.  then if you browse to /mnt, your debian files will be in there

---

### Post by sekinto on 2009-04-02
> **adult swim said:**
> or you can run ```
sudo mount /dev/sdaX /mnt
``` changing sdaX to whatever the debian partition is.  then if you browse to /mnt, your debian files will be in there

/mnt probably isn't a good place to mount a partition, /mnt/afolder would be better.

---

### Post by adult swim on 2009-04-02
difference being?

---

### Post by texas.chef94 on 2009-04-02
I merely wanted to thank each of you who responded. You added considerably to an old mans learning curve.

Allen

---

