---
title: "Desktop as apt source"
date: 2005-06-20
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-20
Yes, despite apt-get being quite cool, there's a lot of stuff it can't get. So i'd like to be able to download .debs and .rpms to my desktop and have it acknowledge that i have them.

Can I add /home/dave/Desktop as an apt source? 

Thanks
Dave

---

### Post by DJ_Max on 2005-06-20
What "stuff" can't you get. It's very rare that applications you are looking for are in the repositories. They are either in the multiverse or backports.

I wouldn't use RPM's, unless you wanna cause trouble. Same goes for using .deb's not made for Ubuntu.

---

### Post by Dave_is_sexy on 2005-06-20
Mplayer

I added this and it didn't work

deb /home/dave/Desktop Local

.. .debs are made for ubuntu. It's practically debian and it has dpkg to manage them with. And it has Alien to translate RPMs

Anyway I want a desktop repository whether I can get stuff online or not.

---

### Post by DJ_Max on 2005-06-20
[QUOTE=Dave_is_sexy]Mplayer

I added this and it didn't work

deb /home/dave/Desktop Local

.. .debs are made for ubuntu. It's practically debian and it has dpkg to manage them with. And it has Alien to translate RPMs
[/QUOTE]
Who told you .deb's were made for Ubuntu? If I'm using a Debian system, and create a .deb binary, do you think it'll work on a different OS?? It may install, but will cause breakage sooner or later. Deb's are NOT made for Ubuntu. They are a package format, which Ubuntu goes by. If I make a  Ubuntu is NOT just debian with the dpkg program(dpkg comes with Debian as well). Alien doesn't translate rpm's, it *TRIES* to covert package formats the best way it can, which only works for a small number of packages.

Do some reading before you start changing configuration, and installing packages not meant for Ubuntu. And get an understanding of the relationship between Ubuntu & Debian.

FYI, mplayer is in the Ubuntu universe/multiverse repos.

For local repositories, which is mainly used for developers, [http://wiki.ubuntu.com/LocalAptGetRepositories](http://wiki.ubuntu.com/LocalAptGetRepositories)

---

### Post by tread on 2005-06-20
Getting back on topic:
[http://familiasanchez.net/~sanchezr/?page=debrepository](http://familiasanchez.net/~sanchezr/?page=debrepository) 

ALso, DJ_Max is right, don't mix debian or ubuntu repos, unless its a really desperate situation. Compiling stuff is a better option. Debs are just a package format, and Ubuntu developers don't use debian packages, they tweak and compile everything on their own. For example, Ubuntu uses Xorg while Debian uses XFree86, so Ubuntu is ahead of Debian here. This may cause problems if you download packages that depend on xfree86. Even the libc version is different I think .. though I could be wrong here.

---

### Post by DJ_Max on 2005-06-20
[QUOTE=tread]
For example, Ubuntu uses Xorg while Debian uses XFree86, so Ubuntu is ahead of Debian here. This may cause problems if you download packages that depend on xfree86. Even the libc version is different I think .. though I could be wrong here.[/QUOTE]
Your correct. Debian developers build there packages against different library versions. Same goes with Xfree86 and Xorg. I believe the libc, which is a very important library is different depending on what release of Debian it's meant for.

---

### Post by shakin on 2005-06-20
What you are looking for to install debs is the program dpkg. I wrote a Gnome script to do it from the GUI and you should be able to find it in the how-to section (name: "Gnome: Install debs from right click menu" or similar).

If you want to do it from source, compile the program normally (./configure && make) but replace the 'sudo make install' command with ' sudo checkinstall' and it will create a deb and install that deb onto your system.

Either dpkg or checkinstall will make that program available in Synaptic if you want to remove it later.

If you really want to run your own repository, just install Apache, setup the right directory structure, then dump debs into that directory.

---

### Post by Dave_is_sexy on 2005-06-20
I think i'll just install debarchiver. I do know about dpkg but it's not the smartest thing in the world.

---

