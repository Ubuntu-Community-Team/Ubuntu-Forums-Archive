---
title: "dpkg was interrupted?"
date: 2006-09-08
forum: Desktop Environments
---

### Post by hc2995 on 2006-09-08
ok i tried to do sudo apt-get install but i got this instead:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

i did ./dpkg --configure -a and got this:

bash: ./dpkq: No such file or directory


how do i fix this?!?!?!?!

---

### Post by hc2995 on 2006-09-08
bump

---

### Post by jISh on 2006-09-08
Uh, are you sure you didn't type ./dpkq?

---

### Post by hc2995 on 2006-09-08
howard@DELL:~$ ./dpkg --configure -a
bash: ./dpkg: No such file or directory
howard@DELL:~$

---

### Post by hc2995 on 2006-09-08
so what do i do now?

---

### Post by sovietfunk on 2006-09-14
Looks like you're typing ```
./dpkg --configure -a
```

Unless you have cd'ed to /usr/bin/ what you should type is ```
dpkg --configure -a
```

otherwise bash will look in the current directory for "dpkg". That's what "./" is telling it to do. Useful often but certainly not here.

---

### Post by Ramses de Norre on 2006-09-14
And run it with sudo, so ```
sudo dpkg --configure -a
```

---

