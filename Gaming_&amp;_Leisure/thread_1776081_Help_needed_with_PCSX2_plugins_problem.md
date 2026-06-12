---
title: "Help needed with PCSX2 plugins problem"
date: 2011-06-05
forum: Gaming &amp; Leisure
---

### Post by Driger on 2011-06-05
HI, first post on here im pretty green when it comes to ubuntu 

Anyways Ive been trying to install PCSX2 in Ubuntu 11.04 (32 bit) and i have run into some problems. Ive been following the directions from this video on youtube ([http://www.youtube.com/watch?v=n-l_U0hk0d4](http://www.youtube.com/watch?v=n-l_U0hk0d4)) but i ran into problems when attempting to install from both the synaptic package manager and the Ubuntu software center.

the message from synaptic package manager was: 

could not mark all packages for instillation or upgrade, the following packages have unresolvable dependencies. make sure that all required repositories are added and enabled in the preferences. 
pcsx2:
depends: pcsx2-plugins but it is not going to be installed

the message from the software center was "Package dependencies cannot be resolved" then in the details section it said;

The following packages have unmet dependencies:
pcsx2: Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
       Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed
       Depends: pcsx2-data (>= 1:0.9.8.0-0ubuntu1) but 1:0.9.8.0-0ubuntu1 is to be installed
       Depends: pcsx2-plugins (>= 1:0.9.8.0-0ubuntu1) but 1:0.9.8.0-0ubuntu1 is to be installed

I thought i already had installed the dependencies using these codes

```
sudo add-apt-repository ppa:gregory-hainaut/pcsx2.official.ppa
``````
sudo apt-get update
```am i missing something?

any help would be greatly appreciated. the most frustrating part is the youtube video made it look so easy but this has taken me hours of searching around for solutions already. :(

---

### Post by M3TAZ3R0 on 2011-06-05
You and me both.

---

### Post by Driger on 2011-06-06
I figured out what to do to fix this......  with a little help from this french ubuntu forum [http://forum.ubuntu-fr.org/viewtopic.php?pid=4575801](http://forum.ubuntu-fr.org/viewtopic.php?pid=4575801)

**Step 1**: was to add this different repository set with this 

```
 sudo add-apt-repository ppa:micove/console
```then update it

```
 sudo apt-get update
```**Step 2**:  open synaptic package manager and remove the ppa:gregory-hainaut/pcsx2.official.ppa repository from the repositories by clicking the settings tab and then clicking the repositories box.

**Step 3**: search pcsx2 add it and boom pcsx2 seemingly in working condition.

Apparently the original repository used was creating the problem. also note that removing the gregory-hainaut one was necessary because the repositories were conflicting or something or other. 

Anyways hopes this works for you M3TAZ3R0. It worked for me;)

Cheers

---

### Post by malevolent on 2011-08-16
Much appreciate!!

I'm in a 64bit environment and I chrooted only to play pcsx2... a pain in the ***... It seems that this ppa works even in 64bits (I installed remotelly, when I'll arrive home I'll try)

Its' strange that gregory doesn't metioned in the pcsx2 forums... lot of time lost by trying to make work his build when micove's one install like a charm.

Thank you very much!

---

### Post by muzakki.ahmad29 on 2012-06-01
But it seems that ppa only release for ubuntu precise, I add it on my lucid then it's not updated pcsx2 package, It's ignored

---

