---
title: "KDE app under Ubuntu"
date: 2005-11-08
forum: Desktop Environments
---

### Post by Ingla on 2005-11-08
Hello.

I asked about this in general and received several answers, all of which indicated that I should be able to run KDE programs in Gnome...or at most...run KDE also.

I'm looking at a program called Kshowmail, which is supposed to let me check mail still on the server and delete it there before downloading my messages (I get lots of spam and viruses). 

The site says it requires KDE 3. Does that mean it won't run in Gnome or that I need to upgrade something. (Using Breezy.) 

Thank you.

---

### Post by mcmuffy on 2005-11-08
It should work in gnome as long as you have any needed libraries installed.

---

### Post by 23meg on 2005-11-08
You can definitely run KDE apps in Gnome. If this app is in the repositories it will be installed along with its dependencies (which will be some KDE base libraries) and you can run it under Gnome as well. If not, you should check its dependencies and manually install them, or find an alternative repository.

---

### Post by Ingla on 2005-11-08
Thanks.

I can't seem to find out what the dependencies for Kshowmail are. Did a Google search, but came up pretty empty.

Anyone know anything about it?

---

### Post by matthewv on 2005-11-08
Never tried it. You should be able to download the source, extract it, and run a ```
./configure
```; then ```
make
```; and then ```
sudo checkinstall
```

---

### Post by 23meg on 2005-11-08
See if converting one of the rpm packages you'll find [here]("http://sourceforge.net/project/showfiles.php?group_id=45904&package_id=45724") to deb via alien helps. To convert, type "sudo alien" followed by the package path.

---

### Post by Kuoi on 2007-04-24
Maybe you can read my message at an other treath , it works for me.
[post2524543]("http://ubuntuforums.org/showthread.php?p=2524543#post2524543")

Kuoi

---

