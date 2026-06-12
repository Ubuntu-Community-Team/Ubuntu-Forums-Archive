---
title: "BZFlag 2.0.2 &quot;Queen of Maybe&quot;"
date: 2005-07-19
forum: Closed Requests
---

### Post by redlabour on 2005-07-19
[http://www.bzflag.org/](http://www.bzflag.org/)

Have fun....

---

### Post by Virtual DarKness on 2005-07-19
Yep I'd like to have this too!

[I've also tried](http://www.ubuntuforums.org/showthread.php?t=30444) to backport it by myself but without success as you can see.. now that I think about it, maybe my problem was related to the missing nvidia drivers "dev" package.. :roll: 

bye,
Giovanni.

---

### Post by ep_ on 2005-07-19
Different servers are available for version 2.  There is quite a big difference between bzflag version 2.0.x and version 1.10.  A bzflag junkie would understand, heh. 

I'm fairly new but I had a bzflag developer help me try to compile it on Ubuntu. We also tried installing the deb package which  is available on Debian In both cases, a newer version of libcurl3 and/or libcurl3-dev is needed. (>= 7.13.1-1).  This, or higher versions of libcurl 3 are available on Debian,  Redhat, Mandriva, Suse etal. but NOT Ubuntu, best I can determine.  Disclaimer: I could be horribly wrong

Btw, Debian package here: [http://packages.debian.org/unstable/games/bzflag](http://packages.debian.org/unstable/games/bzflag)

---

### Post by ep_ on 2005-07-20
[QUOTE=Virtual DarKness]Yep I'd like to have this too!

[I've also tried](http://www.ubuntuforums.org/showthread.php?t=30444) to backport it by myself but without success as you can see.. now that I think about it, maybe my problem was related to the missing nvidia drivers "dev" package.. :roll: 

bye,
Giovanni.[/QUOTE]


I originally had the same problem.

Try this: ./configure --enable-debug LDFLAGS="-lpthread"

---

### Post by jdong on 2005-07-20
2.0.2 in Breezy. Excellent, approved for build.

---

### Post by ep_ on 2005-07-22
[QUOTE=jdong]2.0.2 in Breezy. Excellent, approved for build.[/QUOTE]
 Apoligizes if I'm not supposed to post here, please redirect me.  The category for this sub-forum is "Requests that have been built and uploaded" but you state its  "approved for build".  So I'm confused, do I need to wait for this to get into the backport or can it be installed right now?

I have Hoary, If its ready to be installed, I don't have a clue as to how to install it from a breezy repository as other posts have warned of breakage, etc.  Maybe its ok to install a single package but it thats the case, I need some pointers.

TIA - ep

---

### Post by ep_ on 2005-07-22
[QUOTE=ep_]Apoligizes if I'm not supposed to post here, please redirect me.  The category for this sub-forum is "Requests that have been built and uploaded" but you state its  "approved for build".  So I'm confused, do I need to wait for this to get into the backport or can it be installed right now?

I have Hoary, If its ready to be installed, I don't have a clue as to how to install it from a breezy repository as other posts have warned of breakage, etc.  Maybe its ok to install a single package but it thats the case, I need some pointers.

TIA - ep[/QUOTE]


Nevermind,  I'm starting to figure this stuff out.  Guess it was coming down the pike all  along. Appreciate the community!

I added the new backport-staging  to my sources, updated and installed bzflag 2.0.x  I commented out the additions to my sources.list  afterwards.

I'm happy to report the install went perfect and so far the game  seems to be running like a top.

---

### Post by Gamabunta on 2005-08-03
So how long does it take for something like bzflag to go from staging to main?

---

