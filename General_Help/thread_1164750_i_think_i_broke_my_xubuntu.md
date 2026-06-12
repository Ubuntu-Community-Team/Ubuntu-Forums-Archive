---
title: "i think i broke my xubuntu"
date: 2009-05-19
forum: General Help
---

### Post by nexxis82 on 2009-05-19
i am currentlu running xubuntu 8.10 on a dell insperon 1501 and it was running fine untill thismorning when i tried to install a new version of transmission... bc my old 1 was no ,longer letting me dl stuff..now wen i try to use package manager or anything i get the following message..

E: Type 'rm' is not known on line 66 in source list /etc/apt/sources.list

and under add remove programs i get... 

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

and my system scources frezes up when opens

---

### Post by SoftwareExplorer on 2009-05-20
> **nexxis82 said:**
> and my system scources frezes up when opens

when the sources.list file is opened? or are you talking about the 'software sources' dialogue box?

if not maybe try:
 opening it with ```
gksudo nautilus
```
Go to /etc/apt/
right click on sources.list
Click properties
click the Permissions tab
Make sure the file is owned by 'root'
open the file
Post it here

This is all assuming that Xubuntu has nautilus. If not maybe someone who actually uses Xubuntu could give advice?

---

### Post by jualin on 2009-05-20
> **SoftwareExplorer said:**
> when the sources.list file is opened?

if not maybe try:
 opening it with ```
gksudo nautilus
```
Go to /etc/apt/
right click on sources.list
Click properties
click the Permissions tab
Make sure the file is owned by 'root'
open the file
Post it here

This is all assuming that Xubuntu has nautilus. If not maybe someone who actually uses Xubuntu could give advice?

Xubuntu actually uses thunar so the correct command should be> gksu thunar

---

### Post by evermooingcow on 2009-05-20
Sounds like the the sources file either has a major typo or has become unreadable or doesn't exist (anymore).

post
```
ls -la /etc/apt/sources.lst
```

and
```
cat /etc/apt/sources.lst
```

---

### Post by nexxis82 on 2009-05-20
it says its owned by root i notice i have a file that says scources.list.save and it goes from 0 bytes to 5.4 mb

---

### Post by TransitMan on 2009-05-20
In oder to open the sources list you need to type in the Terminal the following: ```
sudo gedit /etc/apt/sources.list
``` followed by your password and the sources list should open for you.

---

### Post by nexxis82 on 2009-05-20
> **evermooingcow said:**
> Sounds like the the sources file either has a major typo or has become unreadable or doesn't exist (anymore).

post
```
ls -la /etc/apt/sources.lst
```

and
```
cat /etc/apt/sources.lst
```
ls: cannot access ect/apt/sources.lst: No such file or directory



cat: ect/apt/sources.lst: No such file or directory

---

### Post by nexxis82 on 2009-05-20
> **TransitMan said:**
> In oder to open the sources list you need to type in the Terminal the following: ```
sudo gedit /etc/apt/sources.list
``` followed by your password and the sources list should open for you.
sudo: gedit: command not found

---

### Post by nexxis82 on 2009-05-20
is there some way i can system restore to an earlier date? .. i dunno im pretty new to this still

---

### Post by SoftwareExplorer on 2009-05-20
> **evermooingcow said:**
> Sounds like the the sources file either has a major typo or has become unreadable or doesn't exist (anymore).

post
```
ls -la /etc/apt/sources.lst
```

and
```
cat /etc/apt/sources.lst
```

should be


post
```
ls -la /etc/apt/sources.list
```

and
```
cat /etc/apt/sources.list
```
see if that works
(notice the I in list)

---

