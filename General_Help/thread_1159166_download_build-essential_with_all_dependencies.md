---
title: "download build-essential with all dependencies"
date: 2009-05-14
forum: General Help
---

### Post by onegreenparker on 2009-05-14
Hi All,
I don't have a netork connection on my Ubuntu 9.04 machine but I need build-essential and all dependencies to compile the driver for my iBurst USM modem.

Is there anywhere I can download a package and all dependencies?

---

### Post by oldos2er on 2009-05-14
If you have an Ubuntu CD or DVD, you can install build-essential from there. Or if you have internet access on another machine, you could use either Keryx or Apt on Cd.

---

### Post by CatKiller on 2009-05-14
Build essential is on the live cd. Add it as a source and install build-essential in the usual way.

---

### Post by onegreenparker on 2009-05-14
Thanks for the input.

I don't have the live CD, I installed on Win Vista using wubi.exe after extracting the .iso.

What I did was the following:

Installed the patch found under ***/pool/main/p/patch***
Installed ***/pool/main/d/dpkg***

Saved the ***/pool*** directory to ***/home***

cd to ***/home/pool*** 

ran [B][I]dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
[/I][/B]
then added ***deb file:/home/pool ./***

to sources.list

made sure that the CD was not selected as a source using Synaptic

then ***sudo apt-get update***

then used Synaptic to find and install build-essential

Done!

---

