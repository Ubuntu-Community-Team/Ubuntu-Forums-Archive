---
title: "temp Fix for Bug 1166765 - Nvidia users - Unity Launcher &amp; top panel bar missing"
date: 2013-04-24
forum: Desktop Environments
---

### Post by bmullan on 2013-04-24
the bug affects Nvidia users...
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1166765](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1166765)

temp fix is open a terminal <ctrl> <alt> <f1> and execute the following:

$ gsettings reset org.compiz.core:/org/compiz/profiles/unity/plugins/core/ active-plugins
$ shutdown -r now

fixes it but maybe not permanently yet so keep this note handy.

---

