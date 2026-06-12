---
title: "APT and APT-GET"
date: 2020-03-05
forum: Desktop Environments
---

### Post by Geoff_Lane on 2020-03-05
Folks,

Appreciate of late the advice is to use **apt** for program maintenance but I often, out of habit, use **apt-get**

Are these one of the same programs now, do they use the same sources list etc?

Geoff

---

### Post by CelticWarrior on 2020-03-05
Not exactly the same but almost.
Everything uses the same software sources, including the GUI tools.

---

### Post by Frogs Hair on 2020-03-05
See Link[URL="https://askubuntu.com/questions/445384/what-is-the-difference-between-apt-and-apt-get"]
https://askubuntu.com/questions/445384/what-is-the-difference-between-apt-and-apt-get[/URL]

---

### Post by deadflowr on 2020-03-05
A side from the posted link by Frog's Hair
two things noticeably different are

1) apt can install local packages
so you can use it to install downloaded deb packages.
before you had to use either dpkg/apt install -f commands or a gui like gdebi.

2)apt automatically clears out the cached package archives.
When you run apt-get install/upgrade packages are downloaded to the cache directory where they are saved until user interaction to remove.
(This is done withe apt-get clean/autoclean commands)
apt, on the other hand, downloads the package, but when the package is successfully installed the cached package is removed from the system.

This can save a lot of disk space as updates can account for many MBs or even GBs of disk space over the course of any given release.
You can also change this feature to allow apt to still save the cache if you want. So it's not a totally set in stone behavior.
(Which is nice, choice in how something behaves is always good, imho)

---

### Post by Geoff_Lane on 2020-03-07
> **deadflowr said:**
> A side from the posted link by Frog's Hair
two things noticeably different are

1) apt can install local packages
so you can use it to install downloaded deb packages.
before you had to use either dpkg/apt install -f commands or a gui like gdebi.

2)apt automatically clears out the cached package archives.
When you run apt-get install/upgrade packages are downloaded to the cache directory where they are saved until user interaction to remove.
(This is done withe apt-get clean/autoclean commands)
apt, on the other hand, downloads the package, but when the package is successfully installed the cached package is removed from the system.

This can save a lot of disk space as updates can account for many MBs or even GBs of disk space over the course of any given release.
You can also change this feature to allow apt to still save the cache if you want. So it's not a totally set in stone behavior.
(Which is nice, choice in how something behaves is always good, imho)


Thanks for explanation, that has clarified matters.

Geoff

---

### Post by Geoff_Lane on 2020-03-07
Thanks CelticWarrior and Frogs Hair for info.

Geoff

---

### Post by TheFu on 2020-03-07
**apt-get** supports package-name-globbing. **apt** does not.

So when I need to remove network-manager,
```
sudo apt-get purge network-manager*  nm-*
```
works.

Or to clean up old kernels, 
```
sudo apt-get purge linux-image-4.15.0-[0-6]*
```

There are lots of different front-end tools for APT. They all use the same back-end DB.

---

### Post by Geoff_Lane on 2020-03-07
That is useful Fu, thank you.

Geoff

---

### Post by guiverc on 2020-03-07
There are some rarely used features that exist in `apt-get` that are not supported in `apt`.

 Apt handles maybe the core 90-95% of what we do, but on the rare occasion it doesn't like an option I've used, so I switch to `apt-get` (but these won't be common commands, thankfully TheFu gave an example as I only remember when I get an error from `apt`).

---

### Post by TheFu on 2020-03-08
There was an announcement about APT 2.0 yesterday with a list of additions/improvements.  Some aptitude smarts where being included.

Generally, I use apt except when I need package-name globbing **OR** when I need aptitude's special way of providing alternative solutions to dependency problems **OR** when scripting stuff, like our weekly patching for all the systems here. The apt manpage says the interface isn't stable, so shouldn't be used in scripts.

---

