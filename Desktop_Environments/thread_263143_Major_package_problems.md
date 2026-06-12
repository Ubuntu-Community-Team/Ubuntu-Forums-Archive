---
title: "Major package problems"
date: 2006-09-22
forum: Desktop Environments
---

### Post by jcrnan on 2006-09-22
So this is a more or less fresh install of ubuntu. I just installed ndiswrapper to get the net working and I updated the repositories (enabling them universe, multiverse, etc)


Now most programs are simply not installable because of lots of broken packages that or stuff that just cant be downloaded.

for example: silje@kitty:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  wine: Depends: libartsc0 (>= 1.5.2-0) but it is not installable
E: Broken packages

silje@kitty:~$ sudo apt-get install kdelibs
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  kdelibs: Depends: kdelibs4c2a (>= 4:3.5.2-0ubuntu18.1) but it is not going to be installed
           Depends: kdelibs-bin (>= 4:3.5.2-0ubuntu18.1) but it is not going to be installed
E: Broken packages
silje@kitty:~$


It doesnt work installing under synaptic either and I get this error message for lots of programs.

Any help here? I more or less cant do anything at all.

---

### Post by ozorba on 2006-09-22
Tell us what /etc/apt/sources.list looks like.

have you tried :

sudo apt-get update
sudo apt-get upgrade 

first?

--

---

### Post by jcrnan on 2006-09-22
heh, I tried sudo apt-get upgrade and for some reason it crashed my xorg horribly.. not even reconfugiring the xorg.conf helps. It still says it cant find the screen -_-

---

