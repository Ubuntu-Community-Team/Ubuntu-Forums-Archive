---
title: "[SOLVED] Problem with awn"
date: 2008-12-30
forum: General Help
---

### Post by Gtone on 2008-12-30
Hi all i posted this in the begginers section but noone answered so i thought this is a beter place to post. I just installed awn and i like it very much but i can't add the extra applets I downloaded the tar.gz file but i can't figure out how to install it. I tried the SPM but it seems to be some kind of confusion between libraries and when i install the core library awn is uninstalled and cannot be reinstalled unless the core is uninstalled:confused :

Any help??? i am really confussed

---

### Post by andrewsomething on 2008-12-30
If you're trying to install the testing package, you can follow this guide:

[http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

If you are just using the normal Ubuntu repos:

sudo apt-get install awn-applets-c-core awn-applets-c-extra python-awn-extras awn-applets-python-extras awn-applets-python-core

---

### Post by neu2buntu on 2008-12-30
what is the exact name of the core library you are having trouble with?

---

### Post by Gtone on 2008-12-30
Hi andrew and thnx for your help. no i am not trying to install the test version i want the ''normal'' one, i tryed what you told me and this is my terminal 
> gtone@Netbook:~$ sudo apt-get install awn-applets-c-core awn-applets-c-extra python-awn-extras awn-applets-python-extras awn-applets-python-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package awn-applets-c-core
gtone@Netbook:~$

is there a typo in there? :confused:

the library i can't install is 
awn-core-applets-bzr
it says that it's depended on this library libawn0-bzr but it's not going to be installed due to a conflict or something...

i start to lose track...:(

PS
I am running 8.04 hurdy on Acer Aspire One if that can help in anyway...

---

### Post by Gtone on 2008-12-30
ok problem solved :D I had to download the new trunk version of awn did it and everything works fine!!!!

Thnx everyone have a Happy New Year!!!!

---

### Post by neu2buntu on 2008-12-31
happy new year man ....glad you got a-w-n sorted....

---

