---
title: "[SOLVED] KDE 4.1 not starting up after Loggin In"
date: 2008-08-04
forum: Desktop Environments
---

### Post by bineeshm on 2008-08-04
Hi! Friends,

I wanted to try KDE 4.1 in my Ubuntu. First I installed the KUBUNTU via Synaptic, which actually installed KDE 3.5. Per instruction from some forum I ran couple of commands and removed the older version. Then I installed KDE 4.1 by adding, 

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

then ran below commands:

sudo apt-get install kubuntu-kde4-desktop
sudo apt-get install gtk-qt-engine-kde4

After these installations I selected KDM-KDE 4 as the default DM. When restarted the machine I got the KDE Login Screen. Once logged in, the system shows a black progress bar – pause for a while and returned back to the Login Screen. I’m able to login only to Gnome and not able to get into the KDE desktop at all.

Can someone advice what could have went wrong and how can I log into KDE environment?

An issue I have to mention here is when I first installed the KDE, the installation wasn’t completely successful. Konqurer wasn’t installed properly and I get an alert that few packages were broken.


Regards,
B

---

### Post by miteshanand1729 on 2008-08-04
Select gdm in place of kdm then try...
For details read here [http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml]("http://news.softpedia.com/news/How-To-Install-KDE-4-1-On-Ubuntu-8-04-91034.shtml")

i m using this..

---

