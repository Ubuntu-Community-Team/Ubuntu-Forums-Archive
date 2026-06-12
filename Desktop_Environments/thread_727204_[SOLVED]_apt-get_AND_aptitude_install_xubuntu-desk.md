---
title: "[SOLVED] apt-get AND aptitude install xubuntu-desktop FAIL"
date: 2008-03-17
forum: Desktop Environments
---

### Post by snorkytheweasel on 2008-03-17
apt-get install xubuntu-desktop FAILS: 
error = Couldn't find any package xubuntu-desktop

likewise

aptitude install xubuntu-desktop FAILS: 
error = Couldn't find any package whose name or description matched "xubuntu-desktop"

I've tried several CDs 
Ubuntu 7.10 (desktop)
Kubuntu 7.10 (desktop)
Kubuntu 7.10 (server)

It is possible that the route to the proxy server is wrong. When I was installing the software (command line) I fat fingered the proxy server's IP. I corrected that with
export http_proxy=http://aa.bb.cc.dd:3128

Now what?

---

### Post by taurus on 2008-03-17
Also, make sure you have all the repos enable in /etc/apt/sources.list first before you attend to install anything else.

```
cat /etc/apt/sources.list
```

---

### Post by snorkytheweasel on 2008-03-17
That solved it.

Multiple THXs.  ):P

---

