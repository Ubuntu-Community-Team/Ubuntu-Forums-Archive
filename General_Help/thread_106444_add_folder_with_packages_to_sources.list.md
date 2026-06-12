---
title: "add folder with packages to sources.list?"
date: 2005-12-20
forum: General Help
---

### Post by bigblop on 2005-12-20
I have burned the folder /var/cache/apt/archives to a CD-ROM (about 600 MB). On another machine I would like to be able to uses these packages. Is it possible to add the CD-ROM contaning the packages to the sources.list on the other machine?

---

### Post by Sutekh on 2005-12-20
I'm not sure if just burning the contents of /var/cache/apt/archives to CD will work, but you can try.  In Synaptic, you can easily add a CD-ROM to the repositories.  The option should be in settings or preferences somewhere (I hate posting from work/windows).  I don't know how to add it directly to sources.list, I think Synaptic is easier.

Alternatively you could just copy the packages across to the /var/cache/apt/archives folder on the other PC.  

There is also wiki page for making an apt package CD here; [Ubuntu Wiki - Apt Move Howto]("https://wiki.ubuntu.com/AptMoveHowto") - if you want to try that.

---

### Post by ramaswamyps on 2005-12-20
apt-get install xxx.deb-x.x.x.
from current packages directory seems to work that way
it worked for me.
i think all dependency packages if not in the folder it will get from net.
there must be a command to look at the foldaer from apt-get command
apt-cdrom asks 100 questions likw which folder has main ,nonfree etc etc.

---

