---
title: "Zsnes Crash"
date: 2012-08-21
forum: Emulators
---

### Post by Juicy Goodness on 2012-08-21
This past time I installed Zsnes, I completely forgot about the fullscreen problem, and I left it on fullscreen to find that the next time I went to open it, it would simply crash. No big deal, I could just go  find the zsnesw.cfg file and...

Well, NONE of the .cfg's are accessible to me. I've looked with the "Show Hidden Files" option on, and it's come to no avail. I uninstalled the debian package and tried to rebuild it from source, however, when I tried to install it, my terminal was INSISTENT upon reinstalling the existent Zsnes debian package and keeping its settings. -_- I've tried numerous ways to delete the package, etc., but it's all failed. 

Some assistance would be invaluable.

---

### Post by thatguruguy on 2012-08-21
> **Juicy Goodness said:**
> This past time I installed Zsnes, I completely forgot about the fullscreen problem, and I left it on fullscreen to find that the next time I went to open it, it would simply crash. No big deal, I could just go  find the zsnesw.cfg file and...

Well, NONE of the .cfg's are accessible to me. I've looked with the "Show Hidden Files" option on, and it's come to no avail. I uninstalled the debian package and tried to rebuild it from source, however, when I tried to install it, my terminal was INSISTENT upon reinstalling the existent Zsnes debian package and keeping its settings. -_- I've tried numerous ways to delete the package, etc., but it's all failed. 

Some assistance would be invaluable.

This doesn't really answer your issue regarding zsnes, but have you tried bsnes? It's available from [playdeb.net]("http://www.playdeb.net/updates/ubuntu/12.04/?q=bsnes"), and (at least on my machine) works really well.

---

### Post by Juicy Goodness on 2012-08-21
> **thatguruguy said:**
> This doesn't really answer your issue regarding zsnes, but have you tried bsnes? It's available from [playdeb.net]("http://www.playdeb.net/updates/ubuntu/12.04/?q=bsnes"), and (at least on my machine) works really well.
All I've heard is that is only takes .sfc instead of .smc format. Everything I have is in .smc and I don't really trust myself with converting everything correctly.

---

### Post by thatguruguy on 2012-08-21
> **Juicy Goodness said:**
> All I've heard is that is only takes .sfc instead of .smc format. Everything I have is in .smc and I don't really trust myself with converting everything correctly.

There's a tool that handles all of that for you, called snespurify. It's pretty painless to use, and does all the work for you.  You can read about it [here]("http://www.byuu.org/bsnes/user-guide/"). If it's not installed when you first install bsnes, you can get it by installing the "filthypants" repository maintained by hunter kaller. To do so, open a terminal and type the following:
```
sudo add-apt-repository ppa:hunter-kaller/ppa
```
Follow the on-screen prompts. Then, to install snespurify, type the following:
```
sudo apt-get update
sudo apt-get install snespurify
```
After it's installed, just type the following in a terminal:
```
snespurify
```
... and you're good to go.

---

### Post by Juicy Goodness on 2012-08-21
Sweet, thanks.

---

### Post by cupantae on 2012-12-11
Hi there,

> bsnes
Personally, I think there are lots of good reasons to still use zSNES. It seems to me that you only want to know where the configuration files are, correct? They're in .zsnes in your home directory.

On the issue of it crashing on startup, for me, it crashes if I try to start with fullscreen, but not if I start windowed and then make it fullscreen. The easiest way to do this is to run zsnes as:
```
zsnes -v 2
```
-v is the video mode. Try 1 or 0 if 2 doesn't work. You could set a shortcut to this, too.

---

### Post by Open and Sourced on 2012-12-22
zNES is a very marvelous emulation software. It's implementation for old ill-flavored ports turned into a fun, and great emulation. 


I still recommend this for anyone, its contingency will last forever!

---

