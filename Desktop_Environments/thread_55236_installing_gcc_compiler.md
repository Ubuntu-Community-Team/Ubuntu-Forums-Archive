---
title: "installing gcc compiler"
date: 2005-08-08
forum: Desktop Environments
---

### Post by rippon on 2005-08-08
```
user@kubuntu:~$ sudo apt-get install gcc
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
user@kubuntu:~$
?
```
How do I get a c compiler?

---

### Post by varunus on 2005-08-08
Do you have synaptic/kynaptic open?  Do you have another program installing in the background?  If you do, that is why this command will fail with this error.  Reboot if you keep getting this error and you don't have anything else installing or open, or at least log out.

Instead of getting gcc, I recommend you get the "build-essential" package instead; it includes make and autoconf and some other good build stuff.

```
sudo apt-get install build-essential
```

---

### Post by ltmon on 2005-08-08
Well the error message seems to be that you've got another process accessing the apt database.... did you have kynaptic or aptitude open?

To get the compiler and the automake tools etc.  

> sudo apt-get install build-essential

L.

---

