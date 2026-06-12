---
title: "can't install compiz-fusion screensaver plug-in on 9.10"
date: 2010-01-14
forum: Desktop Environments
---

### Post by CyberJutt on 2010-01-14
Hi, I'm new to Linux and have installed Ubuntu 9.10. I was trying to install the screensaver
plugin for compiz-fusoin. I've compiz-fusion installed with the setting manager but I can't able to 
install this plugin. following are the results of my failed attempt to install the plugin:
me@me-desktop:~$ sudo apt-get install git-core automake build-essential intltool libtool python-pyrex python2.5-dev xsltproc compiz-dev compiz-bcop
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git-core is already the newest version.
xsltproc is already the newest version.
Package compiz-bcop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  compiz-fusion-bcop
E: Package compiz-bcop has no installation candidate

please help me by providing the necessary step to install this plugin.

Thanks.

---

### Post by peyu on 2010-02-15
Hey Cyberjust, it seems that you have to install compiz-fusion-bcop instead of compiz-bcop, so just install it with:
```
sudo apt-get install compiz-fusion-bcop
```

and then follow instructions from compiz [http://wiki.compiz.org/Install/PluginsFromGit]("http://wiki.compiz.org/Install/PluginsFromGit") to install screensaver plugin...

---

