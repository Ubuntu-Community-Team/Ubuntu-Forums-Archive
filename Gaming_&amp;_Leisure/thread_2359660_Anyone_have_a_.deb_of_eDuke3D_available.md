---
title: "Anyone have a .deb of eDuke3D available?"
date: 2017-04-26
forum: Gaming &amp; Leisure
---

### Post by strangecrunchy12 on 2017-04-26
I have a copy of Duke Nukem 3D Atomic Edition (CD-ROM) from back in the day, and at the time, I wasn't on Linux.  I have an Ubuntu MATE setup now, and I've been setting up some source ports for other '90s games I have (DOOM, Quake, WOLF3D, SPEAR, etc.), but this is the one game I can't for the life of me get to run, be it with the iccarus .run file, or eduke ( no longer developed for Linux, unfortunately, even thought the site still claims to support it...), and I wasn't mindful enough to pick up a copy of Megaton Edition off of STEAM...so, I'm trying to see if there's anyone out there who might have the most recent debian build of eDuke32 that I might be able to get off of them.  If you're able, it would be MUCH appreciated; I love my old games, and it's great to know that there are so many of my childhood favorites that I can still play, even on Linux.

---

### Post by mastablasta on 2017-04-26
how about on eduke32.com?



otherwise isn't this a DO game? it should run well in dosbox.

---

### Post by strangecrunchy12 on 2017-04-26
You can't get the deb version on eduke32.com anymore ( no longer developed for Linux, unfortunately, even though the site still claims to support it...), hence why I'm looking for a package.  As for DOSBox, I don't want to go that route.  I want the source port for the advanced features, such as high-res texture support and the like.  I don't mean to be rude, but if you're not going to read the whole post, don't bother responding.

---

### Post by oldrocker99 on 2017-04-26
Duke Nukem 3D:Megaton Edition is on Steam for Linux; at least, it's in my library.

---

### Post by strangecrunchy12 on 2017-04-26
Yeah, no, it's no longer on the Steam store, at least not for purchase (if you already bought it, you can still install it and use it as normal), in favor of Duke Nukem 3D 20th Anniversary World Tour, which, sadly, only runs on Windows at present.  It was also taken off of the GOG store.  The only place I can actually get it (physical release), is eBay, and I'm not about to pay $200 because some idiot thinks he or she can make a quick C-bill...which brings me back to the eDuke32 debian package.  Trust me, I've explored EVERY avenue, and there doesn't seem to be any other option that fits my needs other than eDuke32.  The other reason that I don't want to do DOSBox, is that I've already tried it, well, I'm still trying to get it to work as an alternative, but any time I try to launch any DOS executable, it crashes right to desktop.  And I know how to use DOSBox; I use it on my desktop (Windows 10), to use a number of applications I'm used to that just won't run anymore without it.

---

### Post by mastablasta on 2017-04-28
> **strangecrunchy12 said:**
> You can't get the deb version on eduke32.com anymore ( no longer developed for Linux, unfortunately, even though the site still claims to support it...), hence why I'm looking for a package.  As for DOSBox, I don't want to go that route.  I want the source port for the advanced features, such as high-res texture support and the like.  I don't mean to be rude, but if you're not going to read the whole post, don't bother responding.

on their wiki it says the apt repos are no longer maintained. 
[http://wiki.eduke32.com/wiki/APT_repository](http://wiki.eduke32.com/wiki/APT_repository)

on the other hand it also says that they encourage to build from source. there are instruction and all.

[http://wiki.eduke32.com/wiki/Building_EDuke32_on_Linux](http://wiki.eduke32.com/wiki/Building_EDuke32_on_Linux)
[http://wiki.eduke32.com/wiki/Acquiring_the_EDuke32_Source_Code](http://wiki.eduke32.com/wiki/Acquiring_the_EDuke32_Source_Code)

and as i found at least one user that succesfully installed it to Mint in Jan 2017 from source.: [https://forums.duke4.net/topic/8675-eduke32-apt-repository-is-down/](https://forums.duke4.net/topic/8675-eduke32-apt-repository-is-down/)
and a YouTube video of someone running it on linux: [https://www.youtube.com/watch?v=OtxlAls8GFY](https://www.youtube.com/watch?v=OtxlAls8GFY)

 it's a bit hard for me to help more as all gaming sites are blocked where i work.  


furthermore eduke might work in wine. at least the older versions did.


oh and i did read your post, you never mention that you do not want to try the alternative solutions. Which is what you have to do nearly always when using Linux. searchf or alternative solutions. sometimes they are a lot bbetter. sometimes not so much. in this case i though you just wanted to play the game. 

as for dosbox use dbgl to help you launch the programs or launch things from terminal to see the error output.

---

### Post by shanestrife on 2017-12-01
There's one here: [http://debian.orson.at/list_repository/list_repository.php?s=experimental&c=main&a=amd64&p=eduke32](http://debian.orson.at/list_repository/list_repository.php?s=experimental&c=main&a=amd64&p=eduke32)

May not be as up-to-date as building it yourself, but if you just wanted a one-click solution, this should work.

Make sure you put your GRPs in /home/(your username)/.eduke32/. Hope this helps!

---

