---
title: "Cant start handbrake"
date: 2009-01-25
forum: General Help
---

### Post by oddworld on 2009-01-25
On ubuntu 8.04.1 64 bit, I cant get handbrake to run.

```

davis@davis-laptop:~$ ghb
ghb: error while loading shared libraries: libxcb-render-util.so.0: cannot open shared object file: No such file or directory

```

Any ideas?

---

### Post by wolfen69 on 2009-01-25
how did you install handbrake?

---

### Post by wolfen69 on 2009-01-25
update:

uninstall the version you have, and add the following lines to your /etc/apt/sources.list or add them to sources list via system>administration>software sources.

[B]deb [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) hardy main[/B]

then
```
sudo apt-get update
```
then 
```
sudo apt-get install handbrake
```

---

### Post by oddworld on 2009-01-25
The 64 bit deb file on their website.

---

### Post by kostkon on 2009-01-25
It seems that you installed the package offered on Handbrake's site which is only for 8.10. You should remove it.

Because, there is a PPA that offers a package for 8.04 [here]("https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa").

And check here the [relevant thread]("http://ubuntuforums.org/showthread.php?t=992997").

---

### Post by oddworld on 2009-01-25
Bingo

---

