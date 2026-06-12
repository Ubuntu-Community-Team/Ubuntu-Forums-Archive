---
title: "Cannot make and make install in Gnome Shell"
date: 2011-06-20
forum: Desktop Environments
---

### Post by Aventinus on 2011-06-20
I just installed Gnome Shell in Ubuntu 11.04 through [UGR Linux]("http://ugr.teampr0xy.net/install") and everything works fine! The only problem is that I cannot run make and make install. I get the following errors:


```

alexandros@Autobot:~/gnome-shell/source/gnome-shell-extensions$ make && make install
Making all in extensions
make[1]: Entering directory `/home/alexandros/gnome-shell/source/gnome-shell-extensions/extensions'
Making all in alternative-status-menu
make[2]: Entering directory `/home/alexandros/gnome-shell/source/gnome-shell-extensions/extensions/alternative-status-menu'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/alexandros/gnome-shell/source/gnome-shell-extensions/extensions/alternative-status-menu'
Making all in apps-menu
make[2]: Entering directory `/home/alexandros/gnome-shell/source/gnome-shell-extensions/extensions/apps-menu'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/alexandros/gnome-shell/source/gnome-shell-extensions/extensions/apps-menu'
Making all in dock
make[2]: Entering directory `/home/alexandros/gnome-shell/source/gnome-shell-extensions/extensions/dock'
Makefile:434: *** missing separator.  Stop.
make[2]: Leaving directory `/home/alexandros/gnome-shell/source/gnome-shell-extensions/extensions/dock'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alexandros/gnome-shell/source/gnome-shell-extensions/extensions'
make: *** [all-recursive] Error 1

```

Any ideas on what am I missing? 

Thanks in advance!

---

### Post by FormatSeize on 2011-06-20
I have two ideas, but I don't know how right they are. I feel like, at least on my machine, make and make install work only if they happen to feel like it that day. 
 
1. Go to the folder that make goes into right before it throws the `missing seperator. Stop' and check each of the file names. It seems that there is something with the naming of one of them that make is not liking. I ran into something similar the other day, when trying to use a script to turn multiple .deb files to .rpms, and the program would fail if there was a `~' in the name of a file.
 
2. Generally, `make install' needs to be run as root or a user with elevated privileges. I'm not sure how your system is set up, but the line
```
make && make install
```
got my attention in that it's trying to run `make install' without without privileges. But being that it doesn't appear to be getting to the `make install' part, I'm not sure if that's what's causing it.

---

### Post by bmbaker on 2011-06-22
you need to run ```
make && sudo make install
```

---

### Post by mswift on 2011-06-22
There is nothing wrong with your make && make install.
As you can see from your terminal output, alternative-status-menu
and apps-menu extension are installed just fine. 
The problem lies with the dock extension. 

Moreover there is no need to install gnome-shell extensions by using
make and make install, just copy the extension you want to install to
 ~/.local/share/gnome-shell/extensions/

---

