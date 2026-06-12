---
title: "Help working as root at the command line"
date: 2006-09-20
forum: Desktop Environments
---

### Post by notiones on 2006-09-20
Despite my best efforts, I have yet to find an easier way to work with root privelidges other than typing sudo prior to each command. Is it possible to su - so that I do not have to type sudo every time?

Thanks in advance for your help.

Steve

---

### Post by newlinux on 2006-09-20
I think you would just need to give su a password using sudo
```
 sudo passwd root
```

enter your password, then enter what you want for the su password twice.

---

### Post by notiones on 2006-09-20
Thanks. That is exactly what I wanted. I must need some more coffee this am because that is so obvious. 

Thanks again. And, especially for not laughing histerically.

---

### Post by bukwirm on 2006-09-20
Also, 'sudo -i' gives you a root shell.

---

### Post by newlinux on 2006-09-20
> **notiones said:**
> Thanks. That is exactly what I wanted. I must need some more coffee this am because that is so obvious. 

Thanks again. And, especially for not laughing histerically.

You're welcome. I'm sure I've had questions that seemed even simpler. We are all learning here :)

---

### Post by ayoli on 2006-09-20
no need to enable root account you just have to type in:
```
sudo -s -H
```
or ```
sudo -i
``` as said above to have a root shell.
you may want to read that: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by davidshere on 2006-09-20
I use 

sudo sulogin

... and enter the password twice.

---

