---
title: "Does kTorrent run on Ubuntu Gnome desktop"
date: 2006-09-14
forum: Desktop Environments
---

### Post by lamar_air on 2006-09-14
I have a quick question.  I would like to install kTorrent using the package manager.  I'm running Ubuntu 6.06 LTS.  Since this ubuntu version uses the GNOME desktop and kTorrent uses KDE is there a problem or will it still run without any problems?

Thanks

---

### Post by neoeden on 2006-09-14
You can install any kde package on ubuntu using apt-get. 

One thing to note is that you are going to pull in the kdebase libs, which means the first kde app you install is going to install a bunch of other stuff. Another thing to note is that the first KDE application you start after a reboot has to load the kde libraries, which means it will take a bit longer to start. However it will work fine, i use kubuntu and I'm doing the reverse.

---

### Post by lamar_air on 2006-09-14
Say I were to install an app such as kTorrent.  This would install some kde base libs and as you said whenever I first run an app requiring these then it would take a bit longer to load.  

But say you don't have an app running which requires these - then is there any extra overhead for ubuntu which may cause it to run slower?

---

### Post by neoeden on 2006-09-14
From:

[http://wiki.kde.org/tiki-index.php?page=Performance%20Tips](http://wiki.kde.org/tiki-index.php?page=Performance%20Tips)

Since the daemons **automatically terminate after a small delay** when the last KDE application running exits, repeated usage of a single KDE application outside of KDE can make its startup appear longer than it really is.

So yeah, after you stop running ktorrent, kdelibs should unload if nothing else is using em.

---

### Post by lamar_air on 2006-09-14
That's awesome, thanks for your help!

---

### Post by moore.bryan on 2006-09-14
*why ktorrent on gnome?  why not just use bittornado?*

---

### Post by skymt on 2006-09-14
Because KTorrent uses the C++ LibTorrent, while Bittornado uses Python, which is sluggish in comparison.

---

### Post by moore.bryan on 2006-09-14
*"sluggish?"  how slow?  i've tried both and saw no relative difference in speed...*

---

### Post by dolphinsonar on 2006-10-19
I actually prefer Ktorrent to Bittornado and I use gnome 6.06 as well.

Bittornado is not as user friendly, i like the build in search engine on ktorrent as well.  Bittornado is less intuative, and the design shows up kinda wonky.  Purely subjective I suppose.

---

### Post by ashmew2 on 2006-11-08
BitTornado makes the system run ubver slow , it occupies 70% of my 1 gb ram lol , and then no other application opens , so KTorrent is the best bet ull get for torrenting :D

---

