---
title: "Ubuntu cannot be transformed to Kubuntu"
date: 2005-05-27
forum: Desktop Environments
---

### Post by SBarretDolph on 2005-05-27
We installed Ubuntu without problems, or without many problems, but I can't seem to change to Kubuntu. That is switch from Gnome to KDE. Whether I use Synaptic or the install script from the cd I cannot install either konq-addons because it won't install imagemagik.

---

### Post by bored2k on 2005-05-27
[QUOTE=SBarretDolph]We installed Ubuntu without problems, or without many problems, but I can't seem to change to Kubuntu. That is switch from Gnome to KDE. Whether I use Synaptic or the install script from the cd I cannot install either konq-addons because it won't install imagemagik.[/QUOTE]
 What repositories do you have ? Did you install kubuntu-desktop?

---

### Post by SBarretDolph on 2005-05-29
Well, playing with the repositories in synaptic did it. But it seems like I should be able to use the Kubuntu disc to do that.

---

### Post by clb137 on 2005-05-29
[QUOTE=SBarretDolph]Well, playing with the repositories in synaptic did it. But it seems like I should be able to use the Kubuntu disc to do that.[/QUOTE]


have got the cd??? KUbuntu.
They are two different installs, however you can install the any desktop enviorment onto K or the standard Ubuntu release.  

If you just want KDE then download and burn Kubuntu, 

There is no problem in installing KDE onto Ubuntu either, just ensure that your /etc/apt/sources.list  is upto date.

good luck

clinton

---

### Post by JohnC86 on 2005-05-31
noob question: by installing kubuntu, can you choose between Kubuntu/gnome/xfce on the logon screen? I really fancy some Kubuntu but don't want to lose gnome altogether!

---

### Post by shakin on 2005-05-31
[QUOTE=JohnC86]noob question: by installing kubuntu, can you choose between Kubuntu/gnome/xfce on the logon screen? I really fancy some Kubuntu but don't want to lose gnome altogether![/QUOTE]

Yes you can choose between them.

When installing kubuntu-desktop it will ask if you want gdm or kdm as your graphical login app. Either choice is good and you can change again at any time by running 'sudo dpkg-reconfigure kdm'

---

