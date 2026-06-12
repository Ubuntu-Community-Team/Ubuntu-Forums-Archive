---
title: "Balder2d - Zero G shooter (in 2D)"
date: 2006-05-19
forum: Gaming &amp; Leisure
---

### Post by holomorph on 2006-05-19
Hey, 
Just wanted to let people know about my game, balder2d [(balder.sourceforge.net/balder2d)]("http://balder.sourceforge.net/balder2d").

It was originally inspired by the battle room from novel "Ender's game", so if you've read that I'm sure you'll see the influence.  

Anyway, I've posted about it before, but the dependancies formerly made it a bit of a process to install, and since the network stuff was a big part of the problem, and didn't work anyway, I've stripped that out and made a release without those dependancies.  So now it is (I hope) very simple to install:

first, you need to install the dependancies, but now those are all in the repository (at least in dapper) so it's very straight forward:
```

sudo apt-get install libsdl-image1.2 libsdl-mixer1.2 libsdl-gfx1.2-4 libboost-filesystem1.33.1 libguichan0

```

Go to the [sourceforge download page]("http://sourceforge.net/project/showfiles.php?group_id=49631") for balder2d and grab the appropriate  	balder2d_0_9_no_network_*.tar.gz  file for your system (were * is amd64 or i386) and unzip that wherever you want (it contains a single folder, 'bin/' which you probably will want to rename. . sorry about that).  Go to that folder and run the 'balder2d' executable.  

That's all there is to it; I hope it works for Breezy systems as well.  Please let me know if you have problems, or what you think of it.

Thanks
Bjørn

---

### Post by benplaut on 2006-05-19
interesting physics... i'll try it tomorrow (out of here in a min)

---

