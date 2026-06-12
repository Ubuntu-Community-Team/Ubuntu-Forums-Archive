---
title: "Chmod 666 /etc epic fail ?"
date: 2009-06-05
forum: General Help
---

### Post by horia.ancas on 2009-06-05
Hi, this is my first post. I am new to ubuntu, but I am trying to learn. 

I wanted to chmod the etc folder in lampp, but I accidentally typed /etc and suddenly ubuntu freaked out. 
Sudo did not work anymore and also my internet died. In typical windows user fashion, I restarted. After boot, nothing worked anymore :)

Is there anything I can do to fix this ?

Thanx alot ):P

---

### Post by Celauran on 2009-06-05
Try booting from LiveCD, mount your hard drive and sudo chmod 755 /etc from a terminal.

---

### Post by michy99 on 2009-06-05
Boot from a Live CD. Mount drive. chmod /etc (on the mounted drive, not the Live CD one) to 755.

Edit: Wow, in the time it took me to type this, someone else beat me to it.

---

### Post by horia.ancas on 2009-06-05
I will try that, thanks alot :popcorn:

---

### Post by sisco311 on 2009-06-05
Try to boot in Recovery Mode and restore the permissions:
```
chmod 0755 /etc
```

If you can't, then boot a LiveCD, mount the root ("/") partition and restore the permission. 

Assuming that /dev/sda5 is your root partition:
```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda5 /mnt/ubuntu
sudo chmod 0755 /mnt/ubuntu/etc
```

EDIT: Uh, i'm super slow........

---

### Post by horia.ancas on 2009-06-05
Thanks sisco311, recovery mode did the trick.
My Ubuntu is alive and kicking :mrgreen: Beers to everyone ):P

---

