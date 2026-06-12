---
title: "Debian package installation problem"
date: 2005-05-16
forum: Desktop Environments
---

### Post by alex_l on 2005-05-16
Hallo!

I can't install debian paskage! Console error is:
dpkg: error processing /home/alex/skype_1.1.0.3-1_i386.deb (--install):
 failed to open package info file `/var/lib/dpkg/tmp.ci/control' for reading: No such file or directory
Errors were encountered while processing:
 /home/alex/skype_1.1.0.3-1_i386.deb

Where could be problem?

---

### Post by dave9191 on 2005-05-16
Did you run the dpkg with sudo ?

---

### Post by ggozad on 2005-05-16
What command did you issue? Where you root (or sudo)? dpkg -i filename should do it unless the .deb is corrupt.

---

### Post by az on 2005-05-16
To clarify the above two posts:

sudo dpkg -i <package.deb>
If it then complaints about dependancies, do
sudo apt-get -f install.

---

### Post by alex_l on 2005-05-16
O maby mu deb paskage is corupt. When Konqueror downloaded it it onened it in Kate. So after that i just save it! Then it is a problem. I will try to downlod in diferent way. Then replay how it works. Thanks a lot!

---

