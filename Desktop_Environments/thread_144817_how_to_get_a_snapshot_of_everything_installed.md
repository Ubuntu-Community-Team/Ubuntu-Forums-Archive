---
title: "how to get a snapshot of everything installed"
date: 2006-03-15
forum: Desktop Environments
---

### Post by StratosL on 2006-03-15
Hi there. Two quick questions:

1) I was wandering if there is a way to take a snapshot of everything installed on a system and store it in a file (ie every package and version)

2) Is there a way to use the above list with a new install, so that the exact packages are automagically installed on the new machine(s)? 

Thanks, 

Stratos

---

### Post by gborzi on 2006-03-15
[QUOTE=StratosL]Hi there. Two quick questions:

1) I was wandering if there is a way to take a snapshot of everything installed on a system and store it in a file (ie every package and version)

2) Is there a way to use the above list with a new install, so that the exact packages are automagically installed on the new machine(s)? 

Thanks, 

Stratos[/QUOTE]

For 1) type dpkg -l . The answer will be something like this
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                  Version                                  Description
+++-=====================================-========================================-============================================
ii  3ddesktop                             0.2.8-1ubuntu3                           "Three-dimensional" desktop switcher
ii  a2ps                                  4.13b-4.3                                GNU a2ps - 'Anything to PostScript' converte
ii  aatv                                  0.3-1ubuntu1                             A program to watch TV in a text-based consol
ii  abiword
....
As for 2) I would try this:
On the system where you have already installed all packages you wanted type

$ dpkg -l |grep '^ii  '|sed -e 's/ii  //' -e 's/ .*//' > list.txt

move the file list.txt to the other system and type

sudo for i in `cat list.txt`; do
   yes| apt-get install $i
done

but I think there can be better alternatives. Little explanation:
the command dpkg -l |grep '^ii  '|sed -e 's/ii  //' -e 's/ .*//' gives you a list of installed packages without the initial ii, version and description.

---

### Post by StratosL on 2006-03-15
Thanks a lot!

---

### Post by chiskop on 2006-03-16
A bonus question for extra points: 

I would like to do similar as above, except that I have severe bandwidth constraints. How can I update/upgrade two systems with one download? I mean, can I store any downloaded updates for more local installs?

Thanks

---

### Post by GeneralZod on 2006-03-16
[QUOTE=chiskop]A bonus question for extra points: 

I would like to do similar as above, except that I have severe bandwidth constraints. How can I update/upgrade two systems with one download? I mean, can I store any downloaded updates for more local installs?

Thanks[/QUOTE]

All downloaded packages are stored in /var/cache/apt/archives.  Simply copy the contents of this directory to the same directory on the other machines :)

---

