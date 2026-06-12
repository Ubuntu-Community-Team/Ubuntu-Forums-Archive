---
title: "enabling desktop effects xubuntu alternate install help please"
date: 2009-05-07
forum: Desktop Environments
---

### Post by jimlikessweets on 2009-05-07
hey i just followed the guide on distrowatch [http://distrowatch.com/weekly.php?issue=20090504#feature](http://distrowatch.com/weekly.php?issue=20090504#feature) to get a minimal xubuntu install. now i want to enable compiz and it's pretty effects. i don't know which drivers to install or how to get compiz running at login. i use an ati radeon video card. please help

thanks in advanced
-jim

---

### Post by joewski on 2009-05-07
> **jimlikessweets said:**
> hey i just followed the guide on distrowatch [http://distrowatch.com/weekly.php?issue=20090504#feature](http://distrowatch.com/weekly.php?issue=20090504#feature) to get a minimal xubuntu install. now i want to enable compiz and it's pretty effects. i don't know which drivers to install or how to get compiz running at login. i use an ati radeon video card. please help

thanks in advanced
-jim
I don't think compiz works with xubuntu.(Im not 100% sure of the Xcfe desktop).  You need to start with a Gnome desktop or KDE. Gnome is easier.

---

### Post by sisco311 on 2009-05-07
> **jimlikessweets said:**
> hey i just followed the guide on distrowatch [http://distrowatch.com/weekly.php?issue=20090504#feature](http://distrowatch.com/weekly.php?issue=20090504#feature) to get a minimal xubuntu install. now i want to enable compiz and it's pretty effects. i don't know which drivers to install or how to get compiz running at login. i use an ati radeon video card. please help

thanks in advanced
-jim

[http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/]("http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/")

jockey-gtk provides a gtk user interface for configuring drivers:
```
sudo apt-get install jockey-gtk
jockey-gtk
``` 



```

```

---

### Post by evanrmurphy on 2009-05-07
> **joewski said:**
> I don't think compiz works with xubuntu.

This was my impression as well, but maybe it's just not as straightforward as with Ubuntu or Kubuntu. That'd be tite!

:guitar:

---

### Post by DMK62 on 2009-05-07
Compiz will work if you have 3d support for your video card. In Synaptic install compiz and the compiz settings manager, emerald if you want to use emerald themes and also install fusion-icon. Fusion icon can be used to start compiz. Xfce has its own native compositor and that is probably the reason why compiz is not setup like it is with Gnome.

hth

Dale

---

### Post by jimlikessweets on 2009-05-07
> **sisco311 said:**
> [http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/]("http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/")

jockey-gtk provides a gtk user interface for configuring drivers:
```
sudo apt-get install jockey-gtk
jockey-gtk
``` 



```

```

thanks a lot, this did the trick! :o

---

