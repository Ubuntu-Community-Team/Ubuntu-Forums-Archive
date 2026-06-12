---
title: "How do I install programs downloaded from the web?"
date: 2005-04-10
forum: Desktop Environments
---

### Post by Jack Brooks on 2005-04-10
For instance, if I want to install the latest bzflag and it's not in the universe (or any other) repositories, I download it from the web, how do I install it?  Can I use .deb packages?  If so, how do I install those?

Thanks in advance.

---

### Post by humanity_to_others on 2005-04-10
```
cd download_folder
sudo dpkg -i program_name
```

---

### Post by neighborlee on 2005-04-24
[QUOTE=humanity_to_others]```
cd download_folder
sudo dpkg -i program_name
```[/QUOTE]
------------
I was told on #ubuntu  ( someone said they saw it in wiki but I can't verify that) that possibly dev's are working on making it possible to install right from a web download like say fedora or mdk does..mdk is the best at it though as it even works through depdnencies .

you may say there are security risks but i'm sure mdk and fedora ( suse ?) get around it somehow ( same way synaptic does it I imagine but could also (( as was suggested by eurna in #ubuntu)) be done with a special repository that could be maintained.

l8r
neighborlee
-----

---

