---
title: "I broke gcc..."
date: 2006-07-27
forum: Desktop Environments
---

### Post by pollock.tar.gz on 2006-07-27
During installation of VMWare, In a desperate attempt to get it working I did the following:

[from hollywoodb]

> rm /usr/bin/gcc 
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc 
rm /usr/bin/gccbug 
ln -s /usr/bin/gccbug-3.4 /usr/bin/gccbug


DO NOT forget to change the links back after vmware is installed by using the above commands but replacing all instances of "3.4" with "4.0"


i did all of that, but my folders still arent there, and now gcc is broken. any ideas/pointers so i wont have to reinstall? ](*,)

---

### Post by philippe_carlo on 2006-07-27
```

sudo rm /usr/bin/gcc /usr/bin/gccbug 
sudp aptitude reinstall gcc-3.4

```

---

### Post by pollock.tar.gz on 2006-07-27
thanks, but..

setup still doesnt see gcc..is something still wrong?

---

### Post by philippe_carlo on 2006-07-27
I'm sorry, my mistake:
Try
```

sudp aptitude reinstall gcc

```

---

### Post by pollock.tar.gz on 2006-07-27
hey thanks,

not only did that fix it, but now VMWare installs flawlessly. thanks a ton!

---

