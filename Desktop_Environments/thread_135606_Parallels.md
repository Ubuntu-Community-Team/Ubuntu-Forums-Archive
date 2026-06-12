---
title: "Parallels"
date: 2006-02-24
forum: Desktop Environments
---

### Post by rcdeacon on 2006-02-24
I have just installed the .deb file for Parallels 2.1 via Synapic. In the process of configuring Parallels it asks for the linux kernel sources. I have installed everything I know that resembles kernel sources using Synaptic but still it won't install. It's still looking for kernel sources. Does anyone have a clue as to what I am doing wrong?

---

### Post by Who on 2006-02-24
There is a kernel-source package in Synaptic that needs to be unpacked. Install it and then type

cd /usr/src
sudo tar xjvf linux-source-[whatever your kernel is].tar.bz2

at a command line, then wait for a while :)

That ought to work 

Who

---

