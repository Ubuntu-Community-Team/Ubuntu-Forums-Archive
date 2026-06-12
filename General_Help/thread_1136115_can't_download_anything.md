---
title: "can't download anything"
date: 2009-04-24
forum: General Help
---

### Post by RileyRandom on 2009-04-24
i can't download anything, im using ubuntu 9.04. if you need any more info just ask. and please help.


this is the error message when ever i try to download something "Error: Dependency is not satisfiable:"

---

### Post by hikaricore on 2009-04-24
We need more info.

---

### Post by 3Miro on 2009-04-24
I think he means from Add/Remove, but I cannot be sure.

RileyRandom: What are you trying to download?

---

### Post by RileyRandom on 2009-04-24
> **3Miro said:**
> I think he means from Add/Remove, but I cannot be sure.

RileyRandom: What are you trying to download?

im trying to download adobe flash player.

---

### Post by fdrake on 2009-04-24
on the terminal:
sudo apt-get update
 ................
   (and then)
 ................
sudo apt-get install adobe-flashplugin
......................

if there is a problem copy and paste here the terminal message.

---

### Post by RileyRandom on 2009-04-24
> **fdrake said:**
> on the terminal:
sudo apt-get update
 ................
   (and then)
 ................
sudo apt-get install adobe-flashplugin
......................

if there is a problem copy and paste here the terminal message.

here is what it said "riley@ubuntu:~$ sudo apt-get update
[sudo] password for riley: 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release [74.6kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages [4757kB]
Fetched 4831kB in 49s (98.3kB/s)                                               
Reading package lists... Done
riley@ubuntu:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package adobe-flashplugin
riley@ubuntu:~$ 
"

---

### Post by fdrake on 2009-04-24
> 
&#1357;&#1377;&#1392;&#1377;&#1391; wrote on 2009-04-22: (permalink)

so it looks like flashplugin-installer depends on nspluginwrapper and ia32-libs which are present in 'universe' repositry which is not enabled by default.

I assume that the same bug is also present on a newly installed Ubuntu 9.04 system, where by default 'universe' is disabled, and ubufox enables only 'multiverse'.

quotes [from here]("https://bugs.launchpad.net/ubuntu/+source/apturl/+bug/361430")

---

### Post by RileyRandom on 2009-04-24
so do i need to enable universe? if so, how do i do so?

---

### Post by fdrake on 2009-04-24
> sudo apt-get remove flashplugin-installer
sudo apt-get install flashplugin-installer

it seems to work [for them]("http://ubuntuforums.org/showthread.php?p=7135959").. with no extra repos added

if this doesn't work you have to manually add the repositories with synaptic
The package name seems to be flashplugin-installer and not adobe-flashplugin. Using Jaunty RC.

---

