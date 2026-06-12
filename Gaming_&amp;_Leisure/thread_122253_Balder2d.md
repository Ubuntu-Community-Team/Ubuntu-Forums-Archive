---
title: "Balder2d"
date: 2006-01-27
forum: Gaming &amp; Leisure
---

### Post by holomorph on 2006-01-27
Hi,

I just made a new release (version 0.8 ) of [balder2d]("http://balder.sourceforge.net/balder2d/") this time with binaries that should (I hope) work with Ubuntu (download [here]("http://sourceforge.net/project/showfiles.php?group_id=49631")).  

to play you should just need to download and install the guichan and hawkNL .deb packages (gne should only be necesarry if you want to compile).

you also need to install SDL, SDL image, SDL mixer, and boost filesystem:
```
$ sudo apt-get install libsdl1.2 libsdl-image1.2 libsdl-mixer1.2 libboost-filesystem
```

then you just unzip the balder2d archive, and run './balder2d' from the bin directory.  

Let me know how it works (or if it doesn't), and what you think.  Uh, you might want to get a friend or two to play with; there's no AI so it's really only fun to play against your friends on the same computer (you can do network but it only works over LAN really).  

If you want to compile it for some reason (like you're inspiret to help me finish it) there are instructions [here]("http://ubuntuforums.org/showthread.php?t=119265").

---

