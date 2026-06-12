---
title: "Installing glest"
date: 2008-03-01
forum: Gaming &amp; Leisure
---

### Post by gagadude on 2008-03-01
How do you install glest on ubuntu? It comes with a readme but it's not clear enough for an idiot windows user (just switched over!) like me to understand. 
Step by step would be nice! 

I got it here:
[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/RPG/Glest-4083.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/RPG/Glest-4083.shtml)

---

### Post by RKCole on 2008-03-01
Hey.

Don't stress yourself with the package you got; it may be a source code file which may need compiling.  There is an easier way. :)

Just go to [GetDeb]("http://www.getdeb.net/") and search for Glest.  They have version 3.1.0 there s a Ubuntu (.deb) package.  

Take care.

---

### Post by CaptainCabinet on 2008-03-02
> **RKCole said:**
> Hey.

Don't stress yourself with the package you got; it may be a source code file which may need compiling.  There is an easier way. :)

Just go to [GetDeb]("http://www.getdeb.net/") and search for Glest.  They have version 3.1.0 there s a Ubuntu (.deb) package.  

Take care.

I was going to suggest that. :)

---

### Post by RKCole on 2008-03-02
I guess great minds think alike. :)  I wish I could see well enough to play Glest; it looks like a great game.

---

### Post by linq on 2008-03-04
I get the following error when trying to play glest on Gutsy 64 bit after installing the getdeb 3.0.1 package:



ln: creating symbolic link `./configuration.xml' to `/usr/share/games/glest/configuration.xml': File exists
Exception: Can't open propertyMap file: data/lang/english.lng

---

### Post by CaptainCabinet on 2008-03-04
> **RKCole said:**
> I guess great minds think alike. :)  I wish I could see well enough to play Glest; it looks like a great game.

They certainly do. :D
I haven't played Glest myself though I have been wanting to try it as it looks good. Haven't got round to it yet.

---

### Post by hagfish on 2008-03-10
> **linq said:**
> I get the following error when trying to play glest on Gutsy 64 bit after installing the getdeb 3.0.1 package:



ln: creating symbolic link `./configuration.xml' to `/usr/share/games/glest/configuration.xml': File exists
Exception: Can't open propertyMap file: data/lang/english.lng

I got this, too. After footling around for a bit, I uninstalled using Synaptic, then deleted /usr/share/games/glest (requires root privileges) and /home/me/.glest

After reinstalling Glest 3.1.2, it worked great.

---

### Post by Skatertjah on 2008-05-07
Try installing using this method which is probably the easiest way to do it:
Open up an terminal and copy and paste this in there:
```
sudo apt-get install -y --allow-unauthenticated glest glest-data libxerces27
``` Now press enter and it should start installing the game.
I havn't tried it yet but it should work.
I got this from:[ http://ubuntusoftware.info/ubuntu_games/glest.html]("http://ubuntusoftware.info/ubuntu_games/glest.html")
Good luck!

---

### Post by jesuskarol on 2009-05-29
Try this one is libxerces27 does not work


sudo apt-get install -y --allow-unauthenticated glest glest-data libxerces-c28

---

