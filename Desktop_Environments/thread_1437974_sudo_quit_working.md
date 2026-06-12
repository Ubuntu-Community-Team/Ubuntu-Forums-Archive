---
title: "sudo quit working"
date: 2010-03-24
forum: Desktop Environments
---

### Post by sampsont on 2010-03-24
I have a tool flow that executes:
sudo cp -r /home/developer/...  /usr/local/lib

The sudoers file has the following line to make it so the above command will execute without a sudo password:

developer ALL=NOPASSWD: /bin/cp

This has always worked but after installing the Ubuntu updates today, (March 24, 2010), I get the following error message when my script executes the cp command:

```
sudo cp -r /home/developer/projects/m9000/MCU/shared/lib/Linux/i686/* /usr/local/lib
sudo: no tty present and no askpass program specified
```

Is it possible that recent Ubuntu updates to version 9.10 could have broken this?  Any ideas?

Thanks!
todd

---

### Post by macogw on 2010-03-26
Does it work if you specify /bin/cp instead of just cp on the command line?

---

### Post by sampsont on 2010-03-26
It turns out a tool I installed edited my sudoers file and it didn't separate entries with commas like it should have.  I fixed it and all is well.

I appreciate the response!

---

