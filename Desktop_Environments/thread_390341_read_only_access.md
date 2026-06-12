---
title: "read only access?"
date: 2007-03-21
forum: Desktop Environments
---

### Post by k0mpresd on 2007-03-21
i just installed ubuntu last night but i am having a small problem

the only part of the drive i can read/write is /home/$USER..all other files/folders are read-only

how do i change that?

---

### Post by taurus on 2007-03-21
You don't want to change the permissions outside of your $HOME directory.  Doing so will break your system beyond repair.  If you need to edit something, use either sudo or gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by k0mpresd on 2007-03-21
i am trying to install m4-1.4.8

i run:
./configure
make
make install

and this is what i get in terminal:
/usr/bin/install: cannot create regular file `/usr/local/bin/m4': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/k0mpresd/Desktop/m4-1.4.8/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/k0mpresd/Desktop/m4-1.4.8/src'
make: *** [install-recursive] Error 1
k0mpresd@k0mp:~/Desktop/m4-1.4.8$ 

what am i doing wrong?

---

### Post by taurus on 2007-03-21
```

./configure
make
**sudo** make install

```
And use the same password that you logging in with.

---

### Post by k0mpresd on 2007-03-21
that worked

thank you

---

