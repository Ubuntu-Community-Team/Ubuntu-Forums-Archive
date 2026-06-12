---
title: "help me back up stuff."
date: 2009-03-14
forum: General Help
---

### Post by beanco on 2009-03-14
about to leave feisty and go for a fresh installation of intrepid ibex.... or whatever it is called.


i need to back a few things up first though... 

how can I back up 

1. my bookmarks,

2. my emails.

Also, just how are settings usually affected? I assume if I go for a fresh install I will have to make all the settings again.. the wifi stuff, my preferences on the prgms I use...

BUT if I upgrade , version by version until I get up to II, will the settings be saved? would this make sense to do or is it so time consuming that a fresh install would be faster, even with all the new settings to be made.


thanks and sorry for always asking such n00b questions.

robi

---

### Post by dje on 2009-03-15
to backup all of your settings and personal files you must backup your home folder (/home/*username*), you can do this with following command:
```
sudo cp -rvp /home *destination (eg. /media/external_drive)*
```
you can then reinstall and copy your home folder over again

hope this helps,
dje

---

