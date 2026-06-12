---
title: "Using DEB Packages"
date: 2006-02-18
forum: Desktop Environments
---

### Post by gerowen on 2006-02-18
I'm still new to a Debian based system.  How do I run a .deb package?  I'm trying to install AMSN for Ubuntu and it's in this form.

---

### Post by aggiechemist on 2006-02-18
The command in generally sudo dpkg -i /file.deb.

There is an equivalent for redhat packages which is sudo alien -i /file.rpm.

As always, man dpkg can give you some more help.

---

### Post by nalmeth on 2006-02-18
yes, the webcam supported amsn
(assuming the .deb is in your home directory)
APPLICATIONS --> ACCESSORIES --> TERMINAL
```
cd ~/
sudo dpkg -i amsnblahblah.deb
```
Alien is a program that converts .rpm to .deb
```
sudo apt-get install alien
```
Go with debs when you can

---

