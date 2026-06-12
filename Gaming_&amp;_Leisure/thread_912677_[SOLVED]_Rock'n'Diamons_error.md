---
title: "[SOLVED] Rock'n'Diamons error"
date: 2008-09-06
forum: Gaming &amp; Leisure
---

### Post by stinger30au on 2008-09-06
> **speedy55555 said:**
> The list is of favorites from top to bottom:
[B]
rocks'n'dimonds
  
[/B]


how do u install rocks n diamonds so it actually works.???

i have tried countless times and via synaptic. i can find the file and tick itand it added the extra dependancys. it  downloads it.

it does not get added to applications-> games

if i run it from shell i get

Game data not installed!

usage: #dpkg-reconfigure rocksndiamonds
for install/update game levels


so if i run from shell this

 sudo dpkg-reconfigure rocksndiamonds



it asked what to d/l so i tell it what ever i want and i get this error

Update Menu

and returns me to the shell prompt and i go round in circles.

any ideas how to fix??

---

### Post by Perfect Storm on 2008-09-07
*Post split from here: [http://ubuntuforums.org/showthread.php?t=910467](http://ubuntuforums.org/showthread.php?t=910467)*

---

### Post by stinger30au on 2008-09-07
[SIZE=4]yee haw!!!!

i found a fix


[/SIZE][FONT=Arial][SIZE=4]

Type the following command in the terminal window

wget [http://www.artsoft.org/RELEASES/unix/rocksndiamonds/rocksndiamonds-3.2.4.tar.gz](http://www.artsoft.org/RELEASES/unix/rocksndiamonds/rocksndiamonds-3.2.4.tar.gz)

this will download everyhting you need. about 3.5 megabytes or there about

then type this

[/SIZE][/FONT][SIZE=4][FONT=Arial]tar -xvzf rocksndiamonds-3.2.4.tar.gz


this will extract the game in to a new directory

cd to the new directory you just created

cd rocksndiamonds-3.2.4

now to execute this file in this directory do this

[/FONT] ./rocksndiamonds
[/SIZE][FONT=Arial][SIZE=2][SIZE=4]


[/SIZE]
[/SIZE][/FONT]

---

