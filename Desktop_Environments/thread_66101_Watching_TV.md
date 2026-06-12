---
title: "Watching TV"
date: 2005-09-16
forum: Desktop Environments
---

### Post by blockme on 2005-09-16
Hi there,

because the new Release is coming soon I was thinking about switching to Gnome,because I like it more and it seems better supported within the community. 

Now my questions. I was using kubuntu for now. I am trying to switch my applications from kde to gnome. for kontact i am using evolution and an rss reader. firefox i can keep and so on.
the only problem is (even after searching this forum) I cannot find an application for watching TV.

Under KDE i was using Kaffeine and it was working OUT OF THE BOX. within gnome I tried before KDE with myth-tv and everything messed up with mysql and such. is there something similar to kaffeine under gone? e.g. totem plugin?

EDIT: Sorry I forgot about it: I am using a Cinergy 1200 DVB-S card and it seems to be supported by the kernel 2.6.10 by default.

thanks for help!!!!

---

### Post by banadushi on 2005-09-16
I use tvtime for watching TV off my capture card locally.  Its a pretty nice application, and as far as I can tell, desktop environment neutral.

Have a good one,

Jason

---

### Post by blockme on 2005-09-16
Thanks a lot. This looks perfect! I hope there is a package or backport for ubuntu (packages.ubuntu.com seems down).

---

### Post by blockme on 2005-09-21
tvtime is a nice application. it has the best picture in my opinion. but i cannot record with it. is there another program i am able to record with?
i tried myth-tv with my cingergy dvb-s 1200 but I couldn't get it to run. it took lots of time to install it, but i had no idea how to setup my dvb-s card. and i didnt like all these dependencies (mysql is a pain).

---

### Post by frodon on 2005-09-21
i use both tvtime and xdtv. [Xdtv](http://xawdecode.sourceforge.net/)  is a more complete software, it allows to add useful plugins and record, i installed it from synaptic.
If you don't find it in synaptic i will give you some repositories where you could find it.
If i compare the two, i would say that tvtime is maybe easier to use and more intuitive but xdtv is more complete and allow you all that you expect from a tv software.

---

### Post by blockme on 2005-09-21
thanks for this hint (xdtv) but how do you get it installed under Hoary?
Or do I need Breezy for install? it depends on libavcodec2 and this one on libvorbis0a (>= 1.1.0) but I only have 1.0.1 avaiable?

I was using these repositories without luck:

deb [http://xawdecode.sourceforge.net/debian/](http://xawdecode.sourceforge.net/debian/) binary/
deb-src [http://xawdecode.sourceforge.net/debian/](http://xawdecode.sourceforge.net/debian/) source/
deb [ftp://ftp.las.ic.unicamp.br/pub/debian-marillat](ftp://ftp.las.ic.unicamp.br/pub/debian-marillat) unstable main
deb-src [http://perso.wanadoo.fr/debian/](http://perso.wanadoo.fr/debian/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

---

### Post by frodon on 2005-09-21
Use the backport repositories, i can install it with synaptic.
I give you my source.list if it could help you.

---

### Post by blockme on 2005-09-27
your sources lists looks hoary-specific. can i use hoary-backports for breezy as well? just wondering.
or is there a breezy-backport repository?

---

### Post by M4l3k on 2005-09-27
[QUOTE=frodon]i use both tvtime and xdtv. [Xdtv](http://xawdecode.sourceforge.net/)  is a more complete software, it allows to add useful plugins and record, i installed it from synaptic.
If you don't find it in synaptic i will give you some repositories where you could find it.
If i compare the two, i would say that tvtime is maybe easier to use and more intuitive but xdtv is more complete and allow you all that you expect from a tv software.[/QUOTE]

Hi Frodon,

I tried using your backports server but without luck. How do I then proceed? Any alternative servers? ANy other solution?

THanks

M4l3k

---

### Post by frodon on 2005-09-27
I gave my source.list above, i don't know why i can find xdtv with these repositories and not you it's very strange !
Also you can go to the [xawdecode]("http://xawdecode.sourceforge.net/") website and download the .deb, the dependies are also specified but again i don't understand why nobody can't find it in synaptic.

sorry to not help you more

---

