---
title: "Where is ubuntu kernel source directory"
date: 2005-01-27
forum: Desktop Environments
---

### Post by dstrebel on 2005-01-27
I am a newbie I was wondering where the ubuntu kernel source directory is located

---

### Post by albersag on 2005-01-27
[QUOTE=dstrebel]I am a newbie I was wondering where the ubuntu kernel source directory is located[/QUOTE]
 If it is not located in /usr/

You need to install via apt-get

---

### Post by jdodson on 2005-01-27
[QUOTE=dstrebel]I am a newbie I was wondering where the ubuntu kernel source directory is located[/QUOTE]

the kernel source is not on the install cd.  you have to snag it off the main repository(or universe).

if you enable all the repositories in synaptic and do a search for kernel source you should find it.

its somewhere around 50+ megs. 

if you are compiling something that requires the kernel source you can install the linux-headers off the install CD.  that works for most things that require the kernel source, such as drivers or ndiswrapper or the like.

---

### Post by dstrebel on 2005-01-27
I need it to install cisco vpnclient i looked in the respitory there is like nine differnt ones how do I know which one to choose

---

### Post by dstrebel on 2005-01-27
nevermind i figured it out

---

### Post by lloyd on 2005-01-30
Hey,

I'm having trouble installing VPN Client as well, since you made it work with Ubuntu, maybe you could give a few hints?

I've tried installing VPN Client version 4.6, but it won't accept the linux kernel source (the linux-source-2.6.8.1) that I've downloaded with Synaptic.

I need VPN in order to access other services than http at my campus, so I'm quite interested in making this work.

Thanks in advance..

---

