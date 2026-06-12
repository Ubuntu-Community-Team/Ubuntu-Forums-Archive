---
title: "[new] Ubuntu Help Please!!!"
date: 2009-05-11
forum: General Help
---

### Post by AnimeFreak on 2009-05-11
ok I want dual boot xp with 9.04

i have 2 80 gig hard drives 

Slave has Ubuntu (.04 

Master is blank = i want xp on here

will the grub boot loader be affected?

plz help

oh and 1 more thing how do i start a new thread and delete them i fixed the issuse that all the posts below are talking about and i can't seem to start a new thread for this problem......help is greatly apprishiated....

---

### Post by cholericfun on 2009-05-11
1st:
please use a more descriptive title for  a post


to 1.
can you see the partition/ HD under PLACES ?

to 2.
under application- Sound/Video there should be a disc burner

to 3.
theres always an imaginary root user, so thats fine

---

### Post by ArtemZ on 2009-05-11
> 1.) i have a internal hdd and it is called Hot Spot i nolonger have windows and only have ubuntu. how do i force it to mount i have tryied some code but like i said i am new to ubuntu and i think i am missing something.
You should add this device to /etc/fstab, I dont remember how to do that, but this is a right way as I think.
P.S . File /etc/fstab should be edited as root
> 2.) burning Dvds is my life and i have always used nero, ashampoo, and roxio but i notice that ubuntu can use nither or so is there a way for me to be able to make a dvd with menus like i did with the windos programs or am i out of luck
Try Brasero
> 3.) this is just a question no real threat just curious..... why is ther 2 users in the "User and Groups" menu in settings Like "Root" and my account name?
Root is a main administrator, another one is your user, this is same to windows.
>  by the way i don't have  /etc/fstab is this a problem?
It cannot be real ;) Try to edit it as root:
gksudo gedit /etc/fstab

---

### Post by AnimeFreak on 2009-05-11
yes i can

---

### Post by cholericfun on 2009-05-11
> **AnimeFreak said:**
> yes i can


can what?

---

### Post by AnimeFreak on 2009-05-11
ok i am in so what do i edit

---

### Post by AnimeFreak on 2009-05-11
> **ArtemZ said:**
> You should add this device to /etc/fstab, I dont remember how to do that, but this is a right way as I think.
P.S . File /etc/fstab should be edited as root

Try Brasero

Root is a main administrator, another one is your user, this is same to windows.

It cannot be real ;) Try to edit it as root:
gksudo gedit /etc/fstab


ok i have the /etc/fstab open so what do i edit

---

### Post by WatchingThePain on 2009-05-11
Re Burning DVD's. Ubuntu has an app called DEVEDE in the repo's which you might find useful with DVD's alongside Brasero.

---

### Post by AnimeFreak on 2009-05-11
> **WatchingThePain said:**
> Re Burning DVD's. Ubuntu has an app called DEVEDE in the repo's which you might find useful.

i have and brasero but they don't let me make menus like nero or ashampoo

---

### Post by ArtemZ on 2009-05-11
Firstly, you should determine system path to your device. If you have only 2 HDDs in your system (Your main and "Hot Spot") then I think that it's /dev/sdb

---

### Post by cholericfun on 2009-05-11
maybe post the content of fstab here
and while youre at it - also the output from
```
sudo fdisk -l 
```

---

### Post by apparle on 2009-05-11
maybe you are looking for DVD styler
[http://www.dvdstyler.de/](http://www.dvdstyler.de/)

it is available in repositories.
install it from synaptic or use 'sudo apt-get install dvdstyler'

for fstab see this
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by AnimeFreak on 2009-05-11
ok now as far as my hdd i now need to figure out how to get the privilege  to mount it

---

### Post by AnimeFreak on 2009-05-11
bump

---

### Post by bharadwaj on 2009-05-11
DVD Styler is just the software you are looking for
[http://www.dvdstyler.de/index.php?option=com_morfeoshow&task=view&gallery=1&Itemid=61&lang=en](http://www.dvdstyler.de/index.php?option=com_morfeoshow&task=view&gallery=1&Itemid=61&lang=en)

If you are still not satisfied, try the Linux version of Nero!
[http://www.nero.com/eng/linux3.html](http://www.nero.com/eng/linux3.html)

(go for trial before emptying your pockets with a decent price tag from nero) ;)

---

### Post by WatchingThePain on 2009-05-11
> **AnimeFreak said:**
> i have and brasero but they don't let me make menus like nero or ashampoo

DEVEDE lets you make custom menus and personally I find it a lot easier than some of the apps I have tried.

---

### Post by AnimeFreak on 2009-05-11
> **bharadwaj said:**
> 
If you are still not satisfied, try the Linux version of Nero!
[http://www.nero.com/eng/linux3.html](http://www.nero.com/eng/linux3.html)

 
thank u i am so happy now

---

### Post by AnimeFreak on 2009-05-17
i am having a issue installing pixel

it has no .deb 

i got it from the site and it was in a tar.gz file

plz help

---

### Post by AnimeFreak on 2009-05-17
> **AnimeFreak said:**
> i am having a issue installing pixel

it has no .deb 

i got it from the site and it was in a tar.gz file

plz help

bump

---

### Post by AnimeFreak on 2009-05-17
> **AnimeFreak said:**
> bump

bump

---

### Post by AnimeFreak on 2009-05-26
> **AnimeFreak said:**
> bump
bump

---

### Post by AnimeFreak on 2009-06-06
> **AnimeFreak said:**
> ok I want dual boot xp with 9.04

i have 2 80 gig hard drives 

Slave has Ubuntu 9.04 

Master is blank = i want xp on here

will the grub boot loader be affected?

plz help

oh and 1 more thing how do i start a new thread and delete them i fixed the issuse that all the posts below are talking about and i can't seem to start a new thread for this problem......help is greatly apprishiated....

bump

---

### Post by AnimeFreak on 2009-06-06
ok I want dual boot xp with 9.04

i have 2 80 gig hard drives 

Slave has Ubuntu 9.04 

Master is blank = i want xp on here

will the grub boot loader be affected?

plz help

oh and 1 more thing how do i start a new thread and delete them i fixed the issuse that all the posts below are talking about and i can't seem to start a new thread for this problem......help is greatly apprishiated....

---

### Post by AnimeFreak on 2009-06-06
> **AnimeFreak said:**
> ok I want dual boot xp with 9.04

i have 2 80 gig hard drives 

Slave has Ubuntu 9.04 

Master is blank = i want xp on here

will the grub boot loader be affected?

plz help

oh and 1 more thing how do i start a new thread and delete them i fixed the issuse that all the posts below are talking about and i can't seem to start a new thread for this problem......help is greatly apprishiated....

bump

---

