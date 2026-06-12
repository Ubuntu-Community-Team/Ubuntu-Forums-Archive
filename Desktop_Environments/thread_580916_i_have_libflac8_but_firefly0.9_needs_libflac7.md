---
title: "i have libflac8 but firefly0.9 needs libflac7"
date: 2007-10-19
forum: Desktop Environments
---

### Post by themoebius on 2007-10-19
I'm trying to install a feisty version of firefly (mt-daapd_0.9-svn-1676_feisty_i386.deb) and its telling me that it needs libflac7. I checked and I have libflac8 installed, but I don't know how to get version 7.

The website is: [http://nightlies.mt-daapd.org/](http://nightlies.mt-daapd.org/)

What should I do?

Thanks!

---

### Post by Alptraum on 2008-01-25
I had a similar problem trying to manually install ScummVM v0.11.0 which needs libflac7 (oddly enough v0.9.1 uses libflac8 ). libflac7 is a feisty package so you will need to add the feisty repository to your *sources.list* file manually. I added the following two lines and then installed it using the Synaptic Package manager after running *sudo apt-get update*.

```
deb http://za.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://za.archive.ubuntu.com/ubuntu/ feisty main restricted
```

Hope that helps.

---

