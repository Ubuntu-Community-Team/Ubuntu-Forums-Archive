---
title: "Gnome 3"
date: 2011-05-27
forum: Desktop Environments
---

### Post by alex152 on 2011-05-27
Hi everyone!):P

I've just installed gnome 3 on top of ubuntu 11.04 and I have a problem adding extensions:

I've installed the "git" application and cloned the git repository, but when I try to add a new extension using this (for example):

```
./autogen.sh –prefix=$HOME/.local – enable-extensions=”dock”
```
```
make install
```

I get this:

```
alex@alex-Extensa-5630:~/gnome-shell-extensions$ make && sudo make install
Making all in extensions
make[1]: Entering directory `/home/alex/gnome-shell-extensions/extensions'
Making all in user-theme
make[2]: Entering directory `/home/alex/gnome-shell-extensions/extensions/user-theme'
Makefile:434: *** missing separator.  Stop.
make[2]: Leaving directory `/home/alex/gnome-shell-extensions/extensions/user-theme'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alex/gnome-shell-extensions/extensions'
make: *** [all-recursive] Error 1

```

Any ideas?

---

### Post by RLovelett on 2011-05-29
+1
Me too!

According to what I've read it has something to do with a weird tab in the makefile.

---

### Post by Skawt_S on 2011-05-29
I just installed gnome 3, I am wondering if I can get the windows looking the same as they did in unity. I like the layout and enviroment in gnome 3 better but my windows look like there from the 90's. 

Every screen shot I see online has the rounded corners and looks more modern, but mine look like windows 2000. anyone know how to do this? 

I have played around in the gconfig-editor and with the tweak tool but I can not change the actual appearance, only colours.

---

### Post by hal8000 on 2011-05-30
See if gnome-tweak-tool will help:

[http://www.ubuntugeek.com/how-to-fix-common-gnome-3-issues-on-ubuntu-11-04-natty.html](http://www.ubuntugeek.com/how-to-fix-common-gnome-3-issues-on-ubuntu-11-04-natty.html)

---

### Post by bmbaker on 2011-05-30
if you add the testing ppa from ricotz [https://launchpad.net/~ricotz/+archive/testing]("https://launchpad.net/%7Ericotz/+archive/testing")
it will install the base/offical extensions then you can install them from synaptic :-)
you'll need gnome tweak tool too :-)

---

### Post by -unseen- on 2011-05-30
Yes this is a missing tab in front of the indicated line. Just add it to the Makefile and it will compile.

---

### Post by cheebs on 2011-06-07
Sorry, could you show me what the makefile line should look like?
I've added a tab to line 434 but it doesn't make.

---

### Post by alpetric on 2011-06-08
You have to edit the Makefile which caused the error. For example:

```
make[2]: Entering directory `/home/alex/gnome-shell-extensions/extensions/user-theme'
Makefile:434: *** missing separator.  Stop.
```This means that the Makefile in the directory: "gnome-shell-extensions/extensions/user-theme" has a missing seperator in line 434. This is where you have to add the  tab.

Hope this could help

---

