---
title: "Amarok 1.4.5"
date: 2007-03-04
forum: Desktop Environments
---

### Post by geovino on 2007-03-04
How can I install Amarok 1.4.5. I think that's the latest version.

---

### Post by thelostsoul on 2007-03-04
First run these commands:
> wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
sudo apt-key add kubuntu-packages-jriddell-key.gpg

Then add this line to your sources.list:
> deb [http://kubuntu.org/packages/amarok-145](http://kubuntu.org/packages/amarok-145) edgy main

Then do a sudo apt-get update, then sudo apt-get install amarok

---

### Post by geovino on 2007-03-05
Where is sources.list ?

---

### Post by ffxr on 2007-03-05
```
 gksu gedit /etc/apt/sources.list 
```

---

### Post by eeefresh on 2007-03-09
```
Resolving people.ubuntu.com... 82.211.81.132
Connecting to people.ubuntu.com|82.211.81.132|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:30:42 ERROR 404: Not Found.

```

Looks like the site is down..

---

### Post by Grafster on 2007-03-11
The following packages have unmet dependencies:
  amarok: Depends: amarok-xine but it is not going to be installed
          Depends: kdelibs4c2a (>= 4:3.5.3-1) but 4:3.5.2-0ubuntu18.2 is to be installed
          Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
          Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.2 is to be installed
          Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
          Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed
          Depends: libgpod1 (>= 0.4.2) but it is not going to be installed
          Depends: libmysqlclient15off (>= 5.0.24-2) but 5.0.22-0ubuntu6.06.2 is to be installed
          Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.9-0.0ubuntu2 is to be installed
          Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
          Depends: libusb-0.1-4 (>= 2:0.1.12) but 2:0.1.10a-22ubuntu1 is to be installed
E: Broken packages

Same problem as OP. Followed the directions... on dapper.

---

### Post by jimbo99 on 2007-03-11
Amarok is a KDE application.  You are going to have trouble with it until you install whatever is necessary to support it out of the KDE libraries/programs.  One way to do this is to attempt to get KDE to work under Ubuntu.  When that is done you should have a working AmaroK.

Also go to the amarok.kde.org and look up it's dependencies.

---

### Post by Grafster on 2007-03-11
Usually synaptic resolves dependencies though, right?

Since it's finding other, older versions of the libraries I'm assuming that I've got the wrong repositories (or else it's just fundimentally not working with dapper right now)

No?

---

### Post by iamhugeinjapan on 2007-03-11
The Kubuntu.org packages are designed for Edgy.

[http://kubuntu.org/announcements/amarok-1.4.5.php](http://kubuntu.org/announcements/amarok-1.4.5.php)

---

### Post by Grafster on 2007-03-12
Understood.

Thank you!

---

