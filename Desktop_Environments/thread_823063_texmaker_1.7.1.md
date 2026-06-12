---
title: "texmaker 1.7.1 ???"
date: 2008-06-08
forum: Desktop Environments
---

### Post by guano on 2008-06-08
Does anyone knows of .deb for Texmaker 1.7,1?
I've been using Kile, but Texmaker is lightweight, and the new code completion feature makes it quite interesting (this is why I use Kile). I checked and so far, version 1.6 is still the only one available for Ubuntu (even for Intrepid).
The Debian package failed because libqtcore4 (in Debian) is called libqt-core4 in Ubuntu...

---

### Post by ravenon on 2008-06-08
I don't know about a deb, but I just downloaded the source, extracted it, and ran
sudo sh BUILD.sh in the extracted directory. Works like a charm. You will have to have the qt4 development files installed (they go in /usr/share/qt4).

---

### Post by guano on 2008-06-09
Many thanks for your reply, ravenon.

I build it, it is working fine. I also decided to give a try and build a .deb with checkinstall:

[http://www.igc.usp.br/pessoais/guano/temp/texmaker_1.7.1-1_i386.deb](http://www.igc.usp.br/pessoais/guano/temp/texmaker_1.7.1-1_i386.deb)

cheers

---

### Post by luisito on 2008-07-29
Thanks for the package. I installed it and it seems to be working very well.

A mini-bug is that the texmaker icon disappeared from my xfce menu. Of course not a big deal.

---

