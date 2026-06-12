---
title: "Kynaptic &amp; extra repositories --&gt; newer sources"
date: 2005-07-14
forum: Desktop Environments
---

### Post by vedro on 2005-07-14
ellow

I have Installed Kubuntu on my machine and it`s working perfectly. And now I would like to upgrade KDE to 3.4.1, some aplication that I will use for everyday use. I have read the instructions here: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) and updated the repositories. 
But there are nowhere KDE 3.4.1 packages and other newer version of programs. In my "section list" since the extra repositories, has this list grown: now I have similar categoies but some of them are named: (multiverse), (universe).... So I believe that my update of the repositories was a success.

So, could you please tell me where (from which repositories) can i get the latest software/updates?

have a nice day,
vedro

---

### Post by dave9191 on 2005-07-14
The (k)ubuntu versioning system as far as I understand it, is that only certain versions of software are given out with each release of ubuntu and only patched for security reasons. 

So ubuntu 5.04 comes with firefox 1.0.2, and even tho 1.0.4 is out now, ubuntu repositories will not have 1.0.4, just 1.0.2 with security patches. 1.0.4 will be out with the next realease of ubuntu, breezy. Same applies to other things, like kde. 

You might be able to find the latest version in the backports repositories if you enabled them. They contain software taken from development version of ubnutu and ported over to the current version of ubuntu. 

Dave

---

### Post by vedro on 2005-07-14
ellow

*You might be able to find the latest version in the backports repositories if you enabled them. They contain software taken from development version of ubnutu and ported over to the current version of ubuntu.* 

How do I enable backport repositories?

have a nice day,
vedro

---

### Post by dave9191 on 2005-07-14
2 sec on google and viola

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

Dave

---

### Post by skyboy on 2005-07-14
just add :
deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main

or

deb [http://download.kde.org/stable/3.4.1/kubuntu](http://download.kde.org/stable/3.4.1/kubuntu) hoary-updates main

to you /etc/apt/source.list

then sudo apt-get update && sudo apt-get upgrade

---

### Post by GoldBuggie on 2005-07-14
This repository might help

*[http://kubuntu.org/hoary-kde341/](http://kubuntu.org/hoary-kde341/) hoary-updates main *

---

