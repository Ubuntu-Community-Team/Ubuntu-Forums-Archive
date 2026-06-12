---
title: "Automatix"
date: 2005-12-29
forum: Desktop Environments
---

### Post by AllanP on 2005-12-29
Just tried to download automatix from "sudo dpkg -i automatix-ubuntu_4.0-1_i386.deb"
Got the erron 404 not found.
Couldn't find other sources.
Any suggestions?
Thanks

---

### Post by ardchoille on 2005-12-29
[QUOTE=AllanP]Just tried to download automatix from "sudo dpkg -i automatix-ubuntu_4.0-1_i386.deb"
Got the erron 404 not found.
Couldn't find other sources.
Any suggestions?
Thanks[/QUOTE]
I am a regular on an irc channel for Ubuntu and I have seen far too many people having problems with Automatix. The ops there also say Automatix doesn't conform to standards and will break your system. Based on the experiences of so many people, I won't use it.

---

### Post by AllanP on 2005-12-29
[QUOTE=ardchoille]I am a regular on an irc channel for Ubuntu and I have seen far too many people having problems with Automatix. The ops there also say Automatix doesn't conform to standards and will break your system. Based on the experiences of so many people, I won't use it.[/QUOTE]

Well I don't need any additional problems, thanks I won't bother with it.

---

### Post by hashimoto on 2005-12-30
[QUOTE=AllanP]Just tried to download automatix from "sudo dpkg -i automatix-ubuntu_4.0-1_i386.deb"
Got the erron 404 not found.
Couldn't find other sources.
Any suggestions?
Thanks[/QUOTE]

"sudo dpkg -i..." is how you install a downloaded deb package. First you must download the Automatix package.

I've had absolutely no problems with Automatix.

---

### Post by Zalbor on 2005-12-30
I tried it, but it messed up my sources.list somehow (even after I uninstalled it), and even though the stuff in it was correct Synaptic would report error after error. I changed the file with a previous one that I had fortunately saved and needed to apt-get update a number of times before it would work again.

---

### Post by arnieboy on 2005-12-30
[QUOTE=ardchoille]I am a regular on an irc channel for Ubuntu and I have seen far too many people having problems with Automatix. The ops there also say Automatix doesn't conform to standards and will break your system. Based on the experiences of so many people, I won't use it.[/QUOTE]
yes it breaks everyone's system (especially of those on the ubuntu IRC channel who curiously enuf never report their problems to me). for those still interested, herez how to install it:
```
wget http://beerorkid.com/automatix/automatix-ubuntu_4.2-1_i386.deb
sudo dpkg -i automatix-ubuntu_4.2-1_i386.deb

```
the reason he got a 404 was because the old version was removed and a new version put in its place. sometimes, the blind ignorance of most folks on the ubuntu channel irks me to the hilt.
and yes the apt-get errors caused by a freaky planetmirror repo being down has also been fixed in this latest release by simply removing the repo.

---

### Post by arnieboy on 2005-12-30
[QUOTE=Zalbor]I tried it, but it messed up my sources.list somehow (even after I uninstalled it), and even though the stuff in it was correct Synaptic would report error after error. I changed the file with a previous one that I had fortunately saved and needed to apt-get update a number of times before it would work again.[/QUOTE]
next time u get an error, try to report it here instead of drawing ignorant conclusions like "xyz app broke my system"
The reason u were getting the errors was because the planetmirror repos were down. the latest version of automatix has removed those repos.

---

### Post by AllanP on 2005-12-30
[QUOTE=arnieboy]yes it breaks everyone's system (especially of those on the ubuntu IRC channel who curiously enuf never report their problems to me). for those still interested, herez how to install it:
```
wget http://beerorkid.com/automatix/automatix-ubuntu_4.2-1_i386.deb
sudo dpkg -i automatix-ubuntu_4.2-1_i386.deb

```
the reason he got a 404 was because the old version was removed and a new version put in its place. sometimes, the blind ignorance of most folks on the ubuntu channel irks me to the hilt.
and yes the apt-get errors caused by a freaky planetmirror repo being down has also been fixed in this latest release by simply removing the repo.[/QUOTE]

Ok I installed it. Thanks, I'm impressed you wrote the program. Wish I had the brain power to do that. Thanks again and all the best for 2006.

Regards, Allan

---

### Post by hs6705gc on 2005-12-30
Hi!
I'm just curios - is it posssible to aptitude (or apt-get) the Automatix package so it is automatically updated whenever a new version is available (put the package in a repository)?

---

### Post by MButterman on 2005-12-30
With my experiences with Automatix, I found it to be a great package to install and use. If there is any concern about changes in your system I would propose using Easy Ubuntu due to it's uninstall feature.
 
     Needless to say, I share ArnieBoy's frustration in the fact in that it seems easier to say it breaks a system then send him bug reports so he can improve the package's performance. Arnie, keep up the great work and thanks for a great utility. Since this is being developed with your time and without any compensation whatsoever, I appreciate that investment and email me if I can be of any assistance.

Merrill

---

