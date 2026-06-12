---
title: "Can't install flash on Ubuntu 8.04"
date: 2009-02-19
forum: General Help
---

### Post by richj.lfc on 2009-02-19
Basically, every time I try to watch videos etc I'm asked to install flash. So I download it again and install it. It says it's already installed but I reinstall it anyway and it still doesn't work.

I've tried removing it and then reinstalling in the terminal using

```
sudo apt-get install flashplugin-nonfree
```

but it still doesn't work.

Any help would be appreciated.

---

### Post by bumanie on 2009-02-19
Follow [this tutorial]("http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html") - it should work

---

### Post by blazemore on 2009-02-19
Have you tried
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by richj.lfc on 2009-02-20
Tried that tutorial hundreds of times. I removed it in the terminal, then when I tried to install it, it said it was already installed. Here's a screenshot...
[[IMG]http://img6.imageshack.us/img6/3251/flashor3.th.png[/IMG]](http://img6.imageshack.us/my.php?image=flashor3.png)
See it says Reinstall?

Also I entered the code from blazemore's post and loads of stuff happened but unfortunately it didn't make a difference.

Any help, greatly appreciated

[IMG]http://img6.imageshack.us/img6/3251/flashor3.png[/IMG]

---

### Post by 3rdalbum on 2009-02-20
At this point I'd say that there's something wacky going on with your package management system. So bypass the package manager, and install the plugin from the .tar.gz at Adobe.com.

It's pretty much a "drag this file into your /usr/lib/mozilla/plugins directory" sort of install.

---

