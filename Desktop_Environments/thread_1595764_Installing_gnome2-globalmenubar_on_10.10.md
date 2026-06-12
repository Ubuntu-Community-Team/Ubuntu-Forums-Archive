---
title: "Installing gnome2-globalmenubar on 10.10"
date: 2010-10-13
forum: Desktop Environments
---

### Post by localh0st on 2010-10-13
Hello. I tried install Global Menu Bar for some ways (svn, compilation etc.), but it won't finish. Usually it's ending with "error 1" when typing "make", or problems with vala while using svn. 

Somebody could share with .deb package working on 10.10, another method to install it? 
Thanks for replies.

---

### Post by miesogeno on 2010-10-15
same here.

i think it has something to do with maverick repositories not available yet. but i'm a bit of a newbie.

---

### Post by abhishek.kona on 2010-10-17
Yes, the Gnome Global Menu project ([http://code.google.com/p/gnome2-globalmenu/](http://code.google.com/p/gnome2-globalmenu/) ) does not seem to have repositories for Meerkat (10.10)/

---

### Post by Dobbie03 on 2010-10-17
Why not just use the Indicator Applet Application Menu???  Seems to do the same thing.

---

### Post by miesogeno on 2010-10-17
indicator-applet-appmenu has a memory leak. at least in my maverick instalation. it also somehow affects nautilus.

but i got my solution from someone in another topic, just installed globalmenu trough the .deb packages, dependences included. it's working great.

---

### Post by Dobbie03 on 2010-10-17
Glad to hear you got it going, could you tell me where you got those .deb packages from please?

---

### Post by miesogeno on 2010-10-17
i got them from here: [https://launchpad.net/~globalmenu-team/+archive/ppa/+packages](https://launchpad.net/~globalmenu-team/+archive/ppa/+packages)

just expanded the link for lucid ppa, since maverick's not there, and installed the packages one by one, in the "package files" list (just the *i386.deb, for my 32bit distro).

i didn't get them all, just these:

gnome-applet-globalmenu_0.7.9-0ubuntu1~ppa1~lucid2_i386.deb
gnome-globalmenu-common_0.7.9-0ubuntu1~ppa1~lucid2_all.deb 
libglobalmenu-gnome_0.7.9-0ubuntu1~ppa1~lucid2_i386.deb
libgnomenu0-2_0.7.9-0ubuntu1~ppa1~lucid2_i386.de
libgnomenu0-dev_0.7.9-0ubuntu1~ppa1~lucid2_i386.deb

i left out the "transitional package" and the "xfce4". it's working fine.

---

### Post by Dobbie03 on 2010-10-17
Cheers for that!

---

### Post by thongstele on 2010-11-01
> **MattDobson said:**
> Cheers for that!

I install it successfully by running file *.deb in Ubuntu 10.10. But I wonder that how can I add Global menubar into the Panel...I dont see it except for the default Indicator applet appmenu.

Anybody tell me how to add Gnome2-globalemenu in Ubuntu 10.10? (I like Gnome2-globalmenu more than the default Indicatior applet appmenu). 
Thx in advance!

---

### Post by thongstele on 2010-11-01
> **thongstele said:**
> I install it successfully by running file *.deb in Ubuntu 10.10. But I wonder that how can I add Global menubar into the Panel...I dont see it except for the default Indicator applet appmenu.

Anybody tell me how to add Gnome2-globalemenu in Ubuntu 10.10? (I like Gnome2-globalmenu more than the default Indicatior applet appmenu). 
Thx in advance!

haha
After installing all the file *.deb above that miesogeno showed,I log on and I saw Global menu applet...I succeeded. Thx miesogeno so much!

---

