---
title: "Rhythmbox 0.9.2"
date: 2005-11-28
forum: Deferred/Invalid Requests
---

### Post by pulp on 2005-11-28
The sources already appeared in Dapper and although you backported 0.9.1 lately I would really appreciate a backport of this one too.

Thanks so much for your work! (of course not only the backporters but also the rhythmbox team ;) )

---

### Post by strikeforce on 2005-11-29
> 
checking for IPOD... configure: error: iPod explicitly requested but libgpod couldn't be found
make: *** [config.status] Error 1
Build FAILED... 512
Do you want to rebuild w/o dep checks, or get a shell? [Y/s/n] ?s
marc@ubuntu:~/ubp-compile-temp/rhythmbox-0.9.2$ apt-cache search libgpod
marc@ubuntu:~/ubp-compile-temp/rhythmbox-0.9.2$


I can't find libgpod I'm assuming that because its not in breezy it might be able to get done however thats up to jdong

> 
marc@ubuntu:~/ubp-compile-temp$ sudo dpkg -i *deb
Selecting previously deselected package libgpod0.
(Reading database ... 125461 files and directories currently installed.)
Unpacking libgpod0 (from libgpod0_0.2.0-1~breezy0.1_i386.deb) ...
Selecting previously deselected package libgpod-common.
Unpacking libgpod-common (from libgpod-common_0.2.0-1~breezy0.1_i386.deb) ...
Selecting previously deselected package libgpod-dev.
Unpacking libgpod-dev (from libgpod-dev_0.2.0-1~breezy0.1_i386.deb) ...
Setting up libgpod0 (0.2.0-1~breezy0.1) ...

Setting up libgpod-common (0.2.0-1~breezy0.1) ...
Setting up libgpod-dev (0.2.0-1~breezy0.1) ...
marc@ubuntu:~/ubp-compile-temp$


compiles and installs fine so with that installed I can compile rhythmbox 0.9.2, installs and runs fine.  I use xmms so I have nothing linked :) however it connects to podcast? according to the changelog

---

### Post by duffman25 on 2005-11-29
[QUOTE=pulp]The sources already appeared in Dapper and although you backported 0.9.1 lately I would really appreciate a backport of this one too.

Thanks so much for your work! (of course not only the backporters but also the rhythmbox team ;) )[/QUOTE]

I also want this backport ;)
At last, audio cd support is here! Now we can really throw away gnome-cd & make rhythmbox the default cd player.

---

### Post by elleuca on 2005-11-29
What about DAAP (publish and browse Music shares ala iTunes), podcast (connect , listen and downloads podcasts) and audioscrobbler (see [http://last.fm](http://last.fm)) support? 

The only "extern" request should be howl, but those should be disabled by default.

---

### Post by jdong on 2005-11-29
[http://lists.ubuntu.com/archives/ubuntu-backports/2005-November/000474.html](http://lists.ubuntu.com/archives/ubuntu-backports/2005-November/000474.html)

See this reply to the mailing list thread on the same subject.

We'll hold on to this and DEFER it for now, until the mentioned changes are made at the Dapper level.

---

### Post by atom on 2005-12-15
this appears to have been remedied.

---

