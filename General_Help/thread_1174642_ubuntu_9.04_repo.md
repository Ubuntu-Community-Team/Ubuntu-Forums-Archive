---
title: "ubuntu 9.04 repo??"
date: 2009-05-31
forum: General Help
---

### Post by Colo2 on 2009-05-31
Hey, I installed ubuntu 9.04 and I cant seem to install anything:
> sudo apt-get install wine
> tom@tom-ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine
tom@tom-ubuntu:~$ 


I opened the package manager synaptic and all the available packages are already installed? Wine isn't there, AWN isn't there nothing
please enlighten me
Tom

---

### Post by steeleyuk on 2009-05-31
Sounds like you need to enable the extra repositories. Open Synaptic > Click the settings menu > Repositories > Click the Updates tab and make sure the top four checkboxes are ticked.

Then reload the package list.

---

### Post by _Purple_ on 2009-05-31
> **Colo2 said:**
> Hey, I installed ubuntu 9.04 and I cant seem to install anything:



I opened the package manager synaptic and all the available packages are already installed? Wine isn't there, AWN isn't there nothing
please enlighten me
Tom

Can you post the content of /etc/apt/sources.list?

---

### Post by Colo2 on 2009-05-31
thanks very much guys, I followed steeleyuk's steps and it now works perfectly. Cheers :)

---

