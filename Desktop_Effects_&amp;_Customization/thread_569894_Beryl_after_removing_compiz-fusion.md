---
title: "Beryl after removing compiz-fusion"
date: 2007-10-07
forum: Desktop Effects &amp; Customization
---

### Post by Mal1024 on 2007-10-07
I had beryl installed but I decided to try Compiz Fusion. After a while I decided to go back to beryl and uninstalled compiz-fusion. I then reinstalled Beryl and now I have a beryl installation with missing window borders. Aptitude also says that I am missing the package "desktop-effects" which is needed for the ubuntu desktop. Can anyone help get Beryl working again or would it be easier just to reinstall Ubuntu?

---

### Post by Forlong on 2007-10-07
First of all: how did you install Compiz Fusion?

---

### Post by Mal1024 on 2007-10-08
I used apt-get with an extra line in /etc/apt/sources.list, and uninstalled the same way.

---

### Post by Forlong on 2007-10-08
Alright, than you have to remove Emerald completely
```
sudo apt-get remove --purge emerald && sudo apt-get autoremove
```
and you have to make sure that extra line is not in the sources.list anymore.

Then install Emerald again.

---

