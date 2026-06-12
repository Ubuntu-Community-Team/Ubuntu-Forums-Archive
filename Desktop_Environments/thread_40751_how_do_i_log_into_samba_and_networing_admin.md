---
title: "how do i log into samba and networing admin"
date: 2005-06-10
forum: Desktop Environments
---

### Post by themoddingden on 2005-06-10
Hi;
heres the problem I'm having .
I log in to all other areas ok buit when I try to mess with samba or networking admin mode I'm kicked back to the main screen and can't change items i want to change.
I want to make the server have a domain for one and i want to setup it's workgroup if he adds sharing in the store.

---

### Post by mindspin on 2005-06-10
What do you mean with "areas"?
If you speak about kcontrol, start it  via sudo kcontrol

mindspin

---

### Post by Olflo on 2005-06-10
hi,
it seems this problem is a bug in KDE 3.4.0. I am experiencing the same problem.
KDE 3.4.1 has been released. You can download Kubuntu packages from this deb source (add to /etc/apt/sources.list):

deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main

or

deb [http://download.kde.org/stable/3.4.1/kubuntu](http://download.kde.org/stable/3.4.1/kubuntu) hoary-updates main

Apperently, things witk the Admin mode work better then.

Personally, I haven't tried this yet. The workaround with starting Kcontrol as Root works, too.

---

