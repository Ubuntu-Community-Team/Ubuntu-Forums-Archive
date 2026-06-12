---
title: "Migrating from Ubuntu 5.04 to Kubuntu 5.04"
date: 2005-09-05
forum: Desktop Environments
---

### Post by swamytk on 2005-09-05
I am very much satisfied with the Ubuntu's performance and using it for last two months. I want to go for KDE 3.4, which seems to be more fast and eye candy desktop. So I want to migrate from Ubuntu to Kubuntu. I want to retain the system configurations such as services and users and user's data.

Is there any official migration plan for this? or else any tricks and tips to do this smoothly?

---

### Post by sunrex on 2005-09-05
if ya only want 3.4 and not 3.4.1 or 3.4.2

do this

open a terminal

type in sudo apt-get install kubuntu-desktop

that sould do the trick

*edit*

it saves everything from gnome to kde everything from gnome will work. everything sould be the same. accept for the new desktop and apps

---

### Post by swamytk on 2005-09-05
[QUOTE=sunrex]if ya only want 3.4 and not 3.4.1 or 3.4.2

do this

open a terminal

type in sudo apt-get install kubuntu-desktop

that sould do the trick

*edit*

it saves everything from gnome to kde everything from gnome will work. everything sould be the same. accept for the new desktop and apps[/QUOTE]

Thanks for quick reply. A few more clarifications, so that I can try these tonight in my home PC.
1. For apt-get install what is the repository path to be added in sources.list?
2. If I want latest KDE 3.4.2 (or 3.4.1) , what is the way?

---

### Post by sunrex on 2005-09-05
you sould have everything u need for repositorys.

for 3.4.1 or 3.4.2...

[http://www.ubuntuforums.org/showthread.php?t=52499](http://www.ubuntuforums.org/showthread.php?t=52499)

*edit*

you need to do the sudo apt-get install kubuntu-desktop before u do the 3.4.1 or 3.4.2 upgrade couse thouse are ONLY upgrades there not the entire thing..........i think...

---

### Post by mlomker on 2005-09-05
apt-get install kdesktop

If you want all of the regular applications along with KDE.  Afteward I removed all of the gnome-* packages in synaptic along with GDM and gaim.

---

### Post by swamytk on 2005-09-06
[QUOTE=sunrex]
you need to do the sudo apt-get install kubuntu-desktop before u do the 3.4.1 or 3.4.2 upgrade couse thouse are ONLY upgrades there not the entire thing..........i think...[/QUOTE]

Thanks sunrex! I have installed kubuntu desktop just like that as you told. It is as smooth as butter. I enjoy it. Let me try 3.4.2 upgrade also.

[QUOTE=mlomker]
apt-get install kdesktop

If you want all of the regular applications along with KDE. Afteward I removed all of the gnome-* packages in synaptic along with GDM and gaim.
[/QUOTE]

Thanks mlomker, for your tips! shall I do kdesktop update before 3.4.2 update or after that? any suggestions?

---

