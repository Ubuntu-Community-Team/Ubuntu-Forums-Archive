---
title: "problems running apt-get"
date: 2005-11-17
forum: Desktop Environments
---

### Post by gauravnawani on 2005-11-17
Hi, I am new to Ubuntu, Just a while back I installed it and during the installation there was a problem with the installation of one of the 'gstreamer-herms' something package the installer said it is oky to proceed as it can be later resolved.

I am not sure that this is the root of the problem, but now whenever I use 'apt-get' to install packages I get this error. 

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

And when I issue 'dpkg --configure -a' I get this
> dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
Aborted

The Synaptic package manager also suggest running 'dpkg --configure -a' which I can not.

I tried searching the forums but couldnt find any thing useful. :confused: 

I installed Ubuntu 5.10 from a CD.

Any help would be appreciated, thanks!

---

