---
title: "medibuntu packages not showing in synaptic"
date: 2009-01-10
forum: General Help
---

### Post by Bubs on 2009-01-10
So I added the medibuntu repo as instructed on the site.  and got the gpg key and all.  but when I tried to search for w64codecs in synaptic it didn't show up. 

BUT when I open a terminal and type sudo apt-get install w64codecs it acted like it installed the codecs.  but they still don't show up in a synaptic search.  while this isn't a big problem it is an annoyance.  I even checked the repo list from within synaptic and it shows that it is checked and all.

it does install the codecs because I was trying to watch a movie and now the movie plays now.

---

### Post by kostkon on 2009-01-10
Do a
```
sudo apt-get update
```
in a terminal and see if you'll get any error messages.

Also, do
```
apt-cache policy w64codecs
```
to check if the package is installed or not.

---

### Post by mgol on 2009-01-10
Did You hit the "Reload" button in Synaptic before searching for this package? Does it change anything?

---

### Post by Bubs on 2009-01-10
apt-cache says its installed, and I hit reload already but it doesn't change anything

---

