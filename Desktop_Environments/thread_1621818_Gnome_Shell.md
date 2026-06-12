---
title: "Gnome Shell"
date: 2010-11-14
forum: Desktop Environments
---

### Post by gavdari on 2010-11-14
I want to try GNOME Shell on Ubuntu 10.10 Maverick. I try the exact steps mentioned [here]("http://live.gnome.org/GnomeShell") but I receive several errors in the terminal after inserting 'jhbuild build'. The errors look like something like this:

[HTML]make: *** [all] Error 2
*** Error during phase build of gobject-introspection: ########## Error running make   *** [2/28]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 
[/HTML]I tried choosing 2 for a few times but the errors keeps coming at me. What's wrong?

---

### Post by davec64 on 2010-11-14
Got the same error, haven't found a solution yet!

---

### Post by gavdari on 2010-11-15
bump

---

### Post by gunashekar on 2010-11-15
Do you have to build it from scratch?
Have you tried the PPA?
```
sudo add-apt-repository ppa:ricotz/testing
```
```
sudo apt-get update
```

---

### Post by kvant on 2010-11-15
> **gunashekar said:**
> Do you have to build it from scratch?
Have you tried the PPA?
```
sudo add-apt-repository ppa:ricotz/testing
``````
sudo apt-get update
```

That PPA contains Natty package, not Maverick.

---

### Post by gavdari on 2010-11-16
A package called gnome-shell is in the repositories, but it doesn't work. I don't know what is that for. The only thing I found was the tutorial in the gnome shell web page and it doesn't work.

---

### Post by Harry33 on 2010-11-16
> **gavdari said:**
> A package called gnome-shell is in the repositories, but it doesn't work. I don't know what is that for. The only thing I found was the tutorial in the gnome shell web page and it doesn't work.

The gnome-shell_2.31.5 package in Maverick official repositories is based on GTK+ 2 and it works very well. I have that version on one of my setups.

However, I also have a Natty setup, where I use Ricotz PPA (testing). That is an up to date GTK+ 3 version of gnome-shell. It also works very well.

There are some difficulties right now building package gnome-shell. I also have noticed build failures during last few days in ricotz PPA (staging).

---

### Post by gavdari on 2010-11-16
so how should I start gnome-shell after installing from the official maverick repository? the commands in their homepage doesn't work

---

### Post by blackvd on 2010-11-17
I'm running 10.10 also but I used this guide to install it with one click and haven't had any problems yet.

[http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html]("http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html")

---

### Post by Harry33 on 2010-11-17
> **gavdari said:**
> so how should I start gnome-shell after installing from the official maverick repository? the commands in their homepage doesn't work

The best way is to install package gnome3-session from the official packages (Maverick and Natty).
Then, from login window, choose session "Gnome3". After that the Gnome-Shell will start automatically on every boot.
Should you want to change back to Gnome2, choose session "Ubuntu Desktop Environment" from the login window.

---

