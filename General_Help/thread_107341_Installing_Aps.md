---
title: "Installing Aps"
date: 2005-12-22
forum: General Help
---

### Post by morganw25 on 2005-12-22
how would I go about installing this program using the repository.  I am a little confused about how this all works.

[http://www.bnro.de/~schmidjo/](http://www.bnro.de/~schmidjo/)

---

### Post by az on 2005-12-22
Enable the universe repository in synaptic and install it

[http://packages.ubuntu.com/breezy/net/linneighborhood](http://packages.ubuntu.com/breezy/net/linneighborhood)


[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by darth_vector on 2005-12-22
first we want to see if the thing is available in the repositories, so we

```
sudo apt-cache search LinNeighborhood
```

and get the following:

```
linneighborhood - An SMB network browser for Linux and X11.
```

so we know the package name. to install we do:

```
sudo apt-get install linneighborhood
```

and we should be done :)

---

### Post by utterlyjaded on 2005-12-22
[QUOTE=morganw25]how would I go about installing this program using the repository.  I am a little confused about how this all works.

[http://www.bnro.de/~schmidjo/](http://www.bnro.de/~schmidjo/)[/QUOTE]


Try going to System --> Administration --> Synaptic Package Manager   and from there do a search for LinNeighborhood, it might come up, otherwise, you need to add some respositories.  If it does come up right click to Mark for Installization, and then Apply.  Its that easy

---

### Post by morganw25 on 2005-12-22
Wow that was easy.  Thanks

---

