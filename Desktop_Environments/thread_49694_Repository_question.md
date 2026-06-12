---
title: "Repository question"
date: 2005-07-17
forum: Desktop Environments
---

### Post by davidgypsy on 2005-07-17
.

---

### Post by Feanor on 2005-07-17
The way I choosed to change repositories is to edit directly the sources.list file. I prefer this way. So I usually do

```
sudo vi /etc/apt/sources.list
```

and add or remove the repo I want to.

Vi is a text editor not so friendly, you can obtain same results via gedit, nano or whatelse you want, doesn't matter.

You can also install synaptic under kubuntu and use it...

```
sudo aptitude install synaptic
```

---

### Post by davidgypsy on 2005-07-17
[QUOTE=Feanor]The way I choosed to change repositories is to edit directly the sources.list file. I prefer this way. So I usually do

```
sudo vi /etc/apt/sources.list
```

and add or remove the repo I want to.

Vi is a text editor not so friendly, you can obtain same results via gedit, nano or whatelse you want, doesn't matter.

You can also install synaptic under kubuntu and use it...

```
sudo aptitude install synaptic
```[/QUOTE]

I tried to install synaptic with the following result:

david@kubuntudavid:~$ sudo aptitude install synaptic
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
No candidate version found for synaptic
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done

No luck! Any suggestions?

---

### Post by Feanor on 2005-07-17
I think you must edit the sources.list file... Seems like it doesn't search in any repo... 

So look here 

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Add a # comment on the first line (deb cdrom ...) and uncomment the other deb repos

if you don't have gedit installed try using vi or kate or other text editor

---

