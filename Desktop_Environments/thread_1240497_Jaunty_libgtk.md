---
title: "Jaunty libgtk"
date: 2009-08-14
forum: Desktop Environments
---

### Post by shuey79 on 2009-08-14
I'm new to linux and I think I screwed something up. When I login my desktop loads but the panel goes into this loop where it loads and unloads.  I read somewhere to press ctrl+alt+f2 and type in sudo apt-get update && sudo apt-get upgrade. When I do the upgrade I get a bunch of issues such as:
totem-plugins: Depends: libgtk2.0-0(>=2.16.0) 2.12.9-4ubuntu2 is installed
transmission-gtk: Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-4ubuntu3 is installed
tsclient: Depends: libgtk2.0-0(>= 2.16.0) but 2.12.9-4ubuntu3 is installed

....
I get a bunch of others.

Does anyone know what I did and how I could fix it?

---

### Post by warp99 on 2009-08-14
The package version on your system is for Hardy (8.04):

[http://packages.ubuntu.com/hardy/libgtk2.0-0](http://packages.ubuntu.com/hardy/libgtk2.0-0)

And it appears you're trying to update to packages for Jaunty (9.04):

[http://packages.ubuntu.com/jaunty/libgtk2.0-0](http://packages.ubuntu.com/jaunty/libgtk2.0-0)

Do you notice the version numbers? Did you recently install some older packages or are you updating from Hardy to Jaunty?

---

