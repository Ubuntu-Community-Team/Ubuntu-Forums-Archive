---
title: "AWN for Jaunty 9.04"
date: 2009-05-02
forum: Desktop Environments
---

### Post by m3alnemer on 2009-05-02
Hello!

I have been trying to install Avant Windows Navigator for Jaunty, but it won't accept Hardy's source.

and it gives "Broken Package" in the terminal when i want to install it.

Any Idea?

---

### Post by ElevenWarrior on 2009-05-02
why AWN? its not nearly as good as cairo-dock.
here's the source for AWN, (jaunty)
[https://launchpad.net/ubuntu/jaunty/+source/avant-window-navigator](https://launchpad.net/ubuntu/jaunty/+source/avant-window-navigator)
hope this helps

---

### Post by m3alnemer on 2009-05-02
Sorry, but What do i do with those files?

How can i install them?

I am a beginner in the terminal :#

---

### Post by m3alnemer on 2009-05-03
I follow the tutorial on [http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/) , but fails when i got to 
```
make
```

HELP:confused:

---

### Post by medjam8 on 2009-05-03
If you want to install AWN do this:

[LIST=1]
[*]Type this in the terminal: ```
sudo gedit /etc/apt/sources.list
``` And enter your password.
[*]Than add > deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) jaunty main and > deb-src [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) jaunty main to the list and save it.
[*]And now just enter ```
sudo apt-get update
``` and ```
sudo apt-get install **avant-window-navigator-trunk awn-manager-trunk awn-extras-applets-trunk**
```
[/LIST]
And your done.

But if you want to install Cairo-Dock than do this:

[LIST=1]
[*]Go to [this page]("http://developer.berlios.de/project/showfiles.php?group_id=8724") and download the latest (probably stable) .deb files.
[*]First run the** cairo-dock_v...**... file and then the **cairo-dock-plug-ins...**... file and install them.
[/LIST]
And your done (again).

---

### Post by id10twork on 2009-05-03
> **m3alnemer said:**
> Hello!

I have been trying to install Avant Windows Navigator for Jaunty, but it won't accept Hardy's source.

and it gives "Broken Package" in the terminal when i want to install it.

Any Idea?

use synaptic... worked for me! just search for awn (click on the search button, don't do a quick search), and it should have all the core packages and extras.

---

### Post by m3alnemer on 2009-05-03
> **medjam8 said:**
> If you want to install AWN do this:

[LIST=1]
[*]Type this in the terminal: ```
sudo gedit /etc/apt/sources.list
``` And enter your password.
[*]Than add  and  to the list and save it.
[*]And now just enter ```
sudo apt-get update
``` and ```
sudo apt-get install **avant-window-navigator-trunk awn-manager-trunk awn-extras-applets-trunk**
```
[/LIST]
And your done.

But if you want to install Cairo-Dock than do this:

[LIST=1]
[*]Go to [this page]("http://developer.berlios.de/project/showfiles.php?group_id=8724") and download the latest (probably stable) .deb files.
[*]First run the** cairo-dock_v...**... file and then the **cairo-dock-plug-ins...**... file and install them.
[/LIST]
And your done (again).

Great....... worked !!! :)
Thanks a ton

---

### Post by hu016865 on 2009-10-14
hi.
i install 9.04 ubuntu inmy laptop and install [B]Mac OS X 10.5 Leopard in ubuntu .
now every thing is ok but avant windows navigator dont work.
i install it again with your post but dont work again ?
when i had to install [/B][B]Mac OS X 10.5 Leopard in ubuntu 9.04 avant work and i see icons in low my desktop but after restart ubuntu avant windows navigator dont work .
it is my screen shot :

[http://www.zshare.net/image/66929819f376249a/](http://www.zshare.net/image/66929819f376249a/)


[/B]

---

### Post by fabounet on 2009-10-14
try Cairo-Dock, it's a real MacOS-like dock.

---

### Post by hu016865 on 2009-10-14
it is not bad but when i get to desktop bar is hiden.
what i must to do ???

---

### Post by fabounet on 2009-10-15
obviously, don't make the 2 bars overlap !
put one of them on another screen side.

---

### Post by hu016865 on 2009-10-15
my friend avant-windows-navigator dont work but cairo-dock work
but avant is better than cairo. 
i want run and use avant but dont work ????

---

### Post by fabounet on 2009-10-16
> but avant is better than cairo. 
=>
> but I find avant better than cairo
because I personnally think the opposite ;-)
(did you try Cairo-Dock 2.1.1 ? here is the PPA : [https://launchpad.net/~cairo-dock-team/+archive/ppa]("https://launchpad.net/~cairo-dock-team/+archive/ppa")

---

### Post by cocopuffz on 2009-10-21
I keep getting a "no public key available" when I get to the update... any ideas? I tried using the gpg on the site...

---

### Post by raprap30 on 2009-10-21
AWN is included in the Ubuntu Repos. Open Synaptic and search for avant-window-manager

---

