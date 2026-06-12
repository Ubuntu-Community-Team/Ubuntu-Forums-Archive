---
title: "No ./configure"
date: 2006-06-12
forum: Desktop Environments
---

### Post by BoneyOne on 2006-06-12
I'm trying to do my first compile (xfire/gaim) but when following the instructions it says to type ./configure --with-gaim=etc, etc...

Now this failed, did some research it seems it's because I didn't have the build-essential package installed...so, apt-get install and now have it.

Problem is that even after installing the build-essential I still get the error saying "./configure: command not found"

Where and How do I get the ./configure to work?!

---

### Post by Luke Covack on 2006-06-12
okay as I'm a newbie of Linux and Ubuntu myself (fed up with windows) doing my own research cuz I have the same problem you might want to get gcc useing the synaptic just surch for gcc and chose the newest one and see if that helps

---

### Post by Ctrl+Alt+Del on 2006-06-12
build-essentials is a meta-package which includes gcc and some more needed stuff.
Are you sure you're in the right directory? After unpacking the tarball you should have a newly created dir in your home, cd into that (or wherever you untarred it), check wether it contains a configure file, if it does, it's probably not executable, in which case a simple (sudo) chmod +x configure should fix it.

---

