---
title: "Crash during installation of package"
date: 2009-06-16
forum: General Help
---

### Post by JHAx86 on 2009-06-16
I was installing smplayer

sudo apt-get install smplayer

during the installation (95%) my system crashed. After restart my pc, I tried to install again, but then the following error message appears:

Errors was encountered while processing:
 libsvga1
 libggi2
 libggi-target-x
 liblzo2-2
 libopenal1
 ttf-dejavu-extra
 ttf-dejavu
 mplayer
 smplayer

E: Sub-process /usr/bin/dpkg returned an error code (1)

This only can mean corrupt files. I tried apt-get remove smplayer, but it doesn't work. I have no idea how to solve this. Any help appreciated.

Thank you for read.

---

### Post by zvacet on 2009-06-17
First check that you have all repos open.**System>admin>software repositories**>check all except **source** under Ubuntu software and forst two under update tab.Reload.Try to install package again.If you still get errors try typing in terminal

```
sudo dpkg --configure -a
```

or 

```
sudo apt-get -f install
```

---

### Post by JHAx86 on 2009-06-17
I tried what you said but I get the same error all the time. There is a problem with the packages I listed in my first post and I cannot remove, reinstall, reconfigure or purge them.

I tried also:
```

sudo dpkg --remove --force-remove-reinstreq smplayer

```And then install again, but the same error. Always the same packages, the ones were installing/downloading when my system crashed (maybe because of another application, I don't know).

---

### Post by rvm4000 on 2009-06-17
Maybe you should delete those deb packages from /var/cache/apt/archives/ so they get downloaded again.

---

