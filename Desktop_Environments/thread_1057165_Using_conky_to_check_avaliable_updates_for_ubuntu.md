---
title: "Using conky to check avaliable updates for ubuntu"
date: 2009-02-01
forum: Desktop Environments
---

### Post by Major_Kong on 2009-02-01
I've found this script - [http://www.box-look.org/content/show.php/Conky+Debian+Available+Updates?content=95218](http://www.box-look.org/content/show.php/Conky+Debian+Available+Updates?content=95218) - to use with conky. It works but has the draw back of requiring administrative privileges. Other than running conky with sudo, what is there to be done ?

---

### Post by Major_Kong on 2009-02-01
No ideas ?

---

### Post by k3ttc4r on 2009-03-17
you have to edit the sudoers file with

```
sudo visudo
```

and give yourself the privilege of using sudo without a password. should be around line 20. at least it is in linux mint.

---

