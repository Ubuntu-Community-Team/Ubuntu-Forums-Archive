---
title: "Finding Installed packages"
date: 2009-06-19
forum: General Help
---

### Post by raam030 on 2009-06-19
Hi,

I am trying to copy the installed packages (installation files) from /var/cache/apt/archives directory, I had installed many programs, all are still working fine. I could find these packages in the directory then.

But now when I tried copying these packages from the said directory, I found all of them are missing, Now all I could find there are only 3 packages which I installed today, apart from that everything else seems to be disappeared. 

I am wondering if there is a way to find these disappeared packages ??? I am sure that I haven't deleted any of them, and all those programs are working perfect. 

I just want to copy them all to a CD so that I dont need re-download them when I reinstall Ubuntu in machine.

Please help ..

Thank you,
Raam.

---

### Post by ozanamn on 2009-06-19
Hey,

Well there is a few ways of doing this. 

All the programs which you install using Synapatic package manger,apt-get,aptitude have a .Deb file in the following folder

/var/cache/apt/archives

Or if you don't like that there is a program the can do it all for you through a nice GUI. [Here]("http://www.ubuntugeek.com/create-backup-of-all-installed-packages-using-aptoncd-in-ubuntu.html") This program also burns it to a CD and everything. 

Any problems let me know.

Rgds,
Oz

---

### Post by raam030 on 2009-06-19
Hi Ozanamn,

I appreciate your help..

I already have this Apt CD program installed. When I opened /var/cache/apt/archives directory I found the packages I had installed earlier were missing, and I could find only those I installed today..

But still all the programs are working good. Is there any settings which deletes old packages from this directory ??? 

is there a way to retrieve those packages I lost ???


Thank you,

Raam.

---

### Post by wojox on 2009-06-19
You didn't run sudo apt-get clean from the terminal did you?
You could try from the terminal

**whereis** and the name off the app.

Also check synaptic and make sure it's not set to delete files after installation.

---

### Post by ozanamn on 2009-06-19
What version of Ubuntu are you using. Did you use the new Janitor tool? Because deletes all the films in that folder.

Oz

---

