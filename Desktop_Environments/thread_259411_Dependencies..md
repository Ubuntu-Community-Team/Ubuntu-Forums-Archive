---
title: "Dependencies."
date: 2006-09-17
forum: Desktop Environments
---

### Post by brucevangeorge on 2006-09-17
How do I list the dependencies of an application that is already installed?

For example: I would like to remove OpenOffice.. but not just the main packages. I would like to remove all the little programs that it also depends on. (Unless they are used by the system).

Is there a way to do this?

---

### Post by lagagnon on 2006-09-17
man ldd

---

### Post by lamego on 2006-09-17
sudo apt-get install gtkorphan

Gtkorphan will remove every package which is not required by any other package.

You can list packages depedencies with:
```
apt-cache show policy package_name
```

---

### Post by aysiu on 2006-09-17
Next time use *aptitude* to install the program:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

