---
title: "sources.list trouble?"
date: 2005-08-30
forum: Desktop Environments
---

### Post by nickless on 2005-08-30
I used to save my sources.list with ubuntu, so when I went to kubuntu I just used the file I had saved from ubuntu. Is this a problem? Is there a kubuntu specific sources.list?  :neutral: 
 :-? should have thought first instead of deleting it... if there is, can someone please paste it here...

---

### Post by shakin on 2005-08-30
[QUOTE=nickless]I used to save my sources.list with ubuntu, so when I went to kubuntu I just used the file I had saved from ubuntu. Is this a problem? Is there a kubuntu specific sources.list?  :neutral: 
 :-? should have thought first instead of deleting it... if there is, can someone please paste it here...[/QUOTE]
 They use the same repositories, so you're ok. You can also add the repository to upgrade to the latest KDE:

[http://kubuntu.org/hoary-kde-342.php](http://kubuntu.org/hoary-kde-342.php)

---

### Post by nickless on 2005-08-30
*phew :D
k just added deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main
thx :)

---

### Post by nickless on 2005-08-30
kde upgrade will be done with
```
apt-get upgrade
```
right? :D

---

### Post by shakin on 2005-08-30
[QUOTE=nickless]kde upgrade will be done with
```
apt-get upgrade
```
right? :D[/QUOTE]


do an 'apt-get update' first so the packages from the new repository are read. I noticed you had some Konqueror stability problems. The newer KDE fixes that for a lot of people. You'll need to log out and then back in once it's finished upgrading.

Good luck!

---

### Post by nickless on 2005-08-30
of course :D thx :)

---

