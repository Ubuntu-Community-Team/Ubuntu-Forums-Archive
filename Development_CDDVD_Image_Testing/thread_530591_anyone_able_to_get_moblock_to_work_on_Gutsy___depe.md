---
title: "anyone able to get moblock to work on Gutsy ?  depends on libnfnetlink1 isn't there"
date: 2007-08-20
forum: Development CD/DVD Image Testing
---

### Post by kraymore on 2007-08-20
anyone able to get moblock to work on Gutsy ?  depends on libnfnetlink1 which isn't in the gutsy repositories.  

[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

is the page i used to install for ubuntu.  its there just need that one dependency so wont install.  

thank you

---

### Post by smartboyathome on 2007-08-20
That is weird, that package is available in Feisty... you may want to try looking for things related to netfilter in synaptic. Otherwise, I would say your best bet is to compile netfilter from source :(

---

### Post by kraymore on 2007-08-21
i found an edgy package for libfnetlink1. installed the .deb file in gutsy then tried to install moblock and it appeared after i installed the .deb file that, either the repositories were updated since my post, or it simply worked fine, and seemed as if that package were updated too.     very happy it can work without much sweat.  so it can work, somehow.

---

### Post by uljanow on 2007-08-22
libnfnetlink1 was renamed to libnfnetlink0 in Gutsy. I guess moblock packages for Debian Lenny might work  with Gutsy. But there are some Ubuntu packages for gutsy 32-bit of [iplist]("http://ubuntuforums.org/showthread.php?t=530183"), which does a similar task.

---

