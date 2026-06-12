---
title: "Problems installing KDE"
date: 2007-01-26
forum: Desktop Environments
---

### Post by Aleksandersen on 2007-01-26
Hi,

When I try to install KDE I get an error saying: "Depends: kdemultimedia but it is not going to be installed."

How do I fix this so I can try KDE?

---

### Post by taurus on 2007-01-26
What command did you run to install KDE?

---

### Post by Aleksandersen on 2007-01-26
```
$ apt-get install kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  kde: Depends: kdemultimedia (>= 4:3.4.3) but it is not going to be installed
E: Broken packages
```

---

### Post by taurus on 2007-01-26
```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

