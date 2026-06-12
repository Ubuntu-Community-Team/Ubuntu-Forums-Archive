---
title: "Nepomuk new backend fails"
date: 2009-08-08
forum: Desktop Environments
---

### Post by urlacher3292 on 2009-08-08
I recently did a fresh install of jaunty and install KDE 4.3 from the semi-official launchpad ppa. I got desktop search to run and it actually works, but every time I login nepomuk says that it is converting to a new backend, but always fails and re-indexes my home home folder on every login. Is their anyway to convert it to the new backend. This problem did not occur before in jaunty with KDE 4.2.4, but I'm not going backwards over one little error. All help is greatly appreciated.

---

### Post by dandelo on 2009-08-09
> **urlacher3292 said:**
> I recently did a fresh install of jaunty and install KDE 4.3 from the semi-official launchpad ppa. I got desktop search to run and it actually works, but every time I login nepomuk says that it is converting to a new backend, but always fails and re-indexes my home home folder on every login. Is their anyway to convert it to the new backend. This problem did not occur before in jaunty with KDE 4.2.4, but I'm not going backwards over one little error. All help is greatly appreciated.

I confirm this error too.

I'm using Kubuntu Jaunty 9.4 with kde 4.3 final release installed with kubuntu backports repos.

I tried googling a little bit,  but I haven't found nothing.

Thanks for any help.

---

### Post by Gooler on 2009-08-09
Another confirmation here.

Also, if you try to set tags/ratings for example on pictures in dolphin and gwenview they aren't the same (gwenview knows the tags created in dolphin thought), and of course the search by hasTag:"" doesn't work either.

:(

---

### Post by saeid on 2009-10-06
confirm on
kubuntu 9.04
kde 4.3.1

---

### Post by saeid on 2009-10-06
I found solution:
> Maybe if you move (rename): ~/.kde/share/apps/nepomuk/repository/main/ is enough.
[http://kubuntuforums.net/forums/index.php?topic=3102231.msg189178#msg189178]("http://kubuntuforums.net/forums/index.php?topic=3102231.msg189178#msg189178")

---

