---
title: "compiz extra plugins"
date: 2009-09-01
forum: Desktop Environments
---

### Post by nos09 on 2009-09-01
Well, I was wondering if I can install extra plugins of compiz. I mean, I have installed ccsm on my machine but i want some more plugings lets say latest-ones like snow or leave plugins. can any body help me how to find them and install.????

---

### Post by earthpigg on 2009-09-01
the compiz-plugins package contains that, but not the ***latest***.

for the latest, we need to go to compiz: [http://www.compiz.org/](http://www.compiz.org/)

the compiz website seems to only have source code downloads, meaning they expect you to compile from source yourself. 

they provide directions here:

[http://wiki.compiz-fusion.org/Installation](http://wiki.compiz-fusion.org/Installation)

---

### Post by earthpigg on 2009-09-01
there is also the compiz-fusion-plugins-unsupported in the ubuntu repos:

> This package provides an extended collection of plugins, which have received
the least amount of review and are the most likely to be problematic on your
system.

compiz is already buggy as hell, and the stuff in that package almost certainly moreso.

if you want to play with this stuff, please write this down on a piece of paper nearbye to save yourself a headache --

alt+f2, and then
> metacity --replace
that command will disable compiz when the bleeding edge plugins inevitably make your desktop unusable.

this command will turn compiz back on:
alt+f2, and then
> compiz --replace

---

