---
title: "how to remove mix desktop"
date: 2008-05-27
forum: Desktop Environments
---

### Post by arturieto on 2008-05-27
I was able to install xubuntu. when ubuntu 8.04 was released, I used package repositories to upgrade xubuntu and install ubuntu. then later on I download kubuntu and used the KDE as default environment. how to remove the xubuntu application?

please help.

I am arturieto from Philippines.

---

### Post by lswest on 2008-05-27
if you want to remove the whole xubuntu desktop environment and applications do ```
sudo apt-get remove xubuntu-desktop
``` (it's a metapackage with links to all the files used by default in xubuntu).

You may need to also just search for all XFCE apps in synaptic and mark them for removal one by one.

---

### Post by arturieto on 2008-05-28
> **lswest said:**
> if you want to remove the whole xubuntu desktop environment and applications do ```
sudo apt-get remove xubuntu-desktop
``` (it's a metapackage with links to all the files used by default in xubuntu).

You may need to also just search for all XFCE apps in synaptic and mark them for removal one by one.

[http://ubuntuforums.org/newreply.php?do=newreply&p=5054873](http://ubuntuforums.org/newreply.php?do=newreply&p=5054873)

thank you so much.

---

### Post by lswest on 2008-05-28
No problem, i hope it worked for you.

---

