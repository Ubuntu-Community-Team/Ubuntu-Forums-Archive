---
title: "KDE on ubuntu instead of gnome"
date: 2005-08-01
forum: Desktop Environments
---

### Post by floyd27 on 2005-08-01
Hi. I have ubuntu installed the hoary 5.04 with gnome.
is there  a way to use kde?
do i have to download a different version to use kde?
thanx

---

### Post by Kimm on 2005-08-01
just do 'apt-get install kubuntu-desktop' in terminal, the download is somewhat big and might take a while depending on your connection though :)

then just logout and select KDE as your session.

---

### Post by floyd27 on 2005-08-01
Hi.
thanx for the help here.
i tried to paste what you wrote there but it says cannot find kubuntu-desktop.
it did the building dependancy tree , but did not find the download?
any thoughts.
thanx

---

### Post by BanskuZ on 2005-08-01
```
apt-get update
apt-get install kubuntu-desktop
```

Try also adding few sources: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by floyd27 on 2005-08-01
Hey.
an update.
I am connected to the net....But i also have the dvd that i installed with.
I tried both with and without the dvd in the drive.
same thing though
just says 
root@ubuntu:/home/roderick # apt-get install kubuntu-desktop
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
 this is now awhat it is saying, which is different than it was before/??

---

### Post by zAo on 2005-08-01
Do you have Synaptic open? Close it and retry.

---

### Post by floyd27 on 2005-08-01
root@ubuntu:/home/roderick # apt-get update
Reading package lists... Done
root@ubuntu:/home/roderick # apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop

this is what i was getting. i restated..
I dont know how to add those things you were talking about.
i went to the link and was immeadetely lost :) ??

---

### Post by floyd27 on 2005-08-01
Hi.
got the update thing you sent me. I was able to get all that, and do the update.
it is now installing the kde one, but i think off the dvd...As it told me to inset it? but it seems to be working so ill let you knwo how it goes.
thanx a bunch.. much apprechiated

---

### Post by ghostintheshell on 2005-08-02
Hi!

I also use those repos:

deb [http://kubuntu.org/](http://kubuntu.org/) hoary-updates main
deb [http://kubuntu.org/hoary-kde342/](http://kubuntu.org/hoary-kde342/) hoary-updates main

Enjoy.

---

