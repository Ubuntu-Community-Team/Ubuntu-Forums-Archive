---
title: "Dark Chess .deb anyone?"
date: 2008-04-26
forum: Gaming &amp; Leisure
---

### Post by H3retic on 2008-04-26
Hey linux gamers.  I have a **quest** for you.

I just found this interesting new game called [COLOR="Red"]Dark Chess[/COLOR].  It's just like regular chess, with the addition of 'fog of war'.  In short, you can't see what's on the squares non adjacent to your players possible moves.

Looks fun, but the only install is in .tar.gz format.  Could anyone build a . deb version, for us less knowledgeable ubuntu fans?

Here are the links:
[Homepage]("http://www.silvertreerpg.org/dark/")
[.tar.gz Download]("http://happypenguin.org/show?Dark%20Chess%20960")

---

### Post by Perfect Storm on 2008-04-26
There not much to build yet.
Here what you do;

Doenload the source to your Desktop

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential
cd ~/Desktop
tar zxfv dark-chess.tar.gz
cd dark-chess
sh build.sh
./dark
```

---

### Post by CREEPING DEATH on 2008-04-27
> **Artificial Intelligence said:**
> There not much to build yet.
Here what you do;

Doenload the source to your Desktop

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential
cd ~/Desktop
tar zxfv dark-chess.tar.gz
cd dark-chess
sh build.sh
./dark
```

Isn't there something called 'checkinstall' or something that makes this easier?

CD

---

### Post by Perfect Storm on 2008-04-27
You can't use checkinstall on everything. It requires that source codes comes with configure scripts and some other stuff.
Other compiling methode like scons/python/or simply a make script it won't work. Also using checkinstall can sometimes be unreliable not moving the files correct or give wrong permissions.

Dark-chess comes with a little script so you can launch it. That's it. Notable it looks pre-alpha.

---

### Post by Scarath on 2008-04-27
You could use 'alien' to convert it to a .deb file.

---

### Post by Perfect Storm on 2008-04-27
> **Scarath said:**
> You could use 'alien' to convert it to a .deb file.

That's a 50/50 situation - can also be dangerous as redhat put stuff diffrently than Debian and may have diffrent scripts etc.

Also why Checkinstall can be dangerous: [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by H3retic on 2008-04-28
> **Artificial Intelligence said:**
> There not much to build yet.
Here what you do;

Doenload the source to your Desktop

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential
cd ~/Desktop
tar zxfv dark-chess.tar.gz
cd dark-chess
sh build.sh
./dark
```

Thanks!

> **Scarath said:**
> You could use 'alien' to convert it to a .deb file.

Also thanks! Looks very useful.

---

