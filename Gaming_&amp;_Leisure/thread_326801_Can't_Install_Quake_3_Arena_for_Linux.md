---
title: "Can't Install Quake 3 Arena for Linux"
date: 2006-12-28
forum: Gaming &amp; Leisure
---

### Post by pajomoro on 2006-12-28
i've download Quake 3 Arena for linux and when i tried to install it he returne this:

cd /cdrom
sh setup.sh
setup.sh: 9: function: not found
x86

in line 9 of setup.sh :
function DetectARCH {

i'm a a beginner on Linux (1 month user) and this may be a stupid question but i realy need a hand on this.

---

### Post by bagofchickens on 2006-12-28
Search google for this installer **linuxq3apoint-1.32b.x86.run**, it should work fine.
Also, I suggest having a look at [http://ioquake3.org/]("http://ioquake3.org/"). The original binaries are rock solid but ioq3 gets better and better, definitely worth a try.

---

### Post by Homunculi on 2007-01-21
it was easy on my system ... 
quake 2 was the hard one  you need to create a directory (i.e.) /usr/local/games/quake3/baseq3

copy copy the .pak files over the the baseq3 directory and then use the .run package 
mentioned in the last thread 

after the install do not launch from the end of the installer 
change directory to the installed directory  and command: quake3 

worked on mine  
or you can use wine and just copy the windows installed directory to /usr/local/games/quake3
after wine is set up  change dir to quake3 and command : wine quake3

---

### Post by pharcyde on 2007-01-21
Have a look at this it may help you. [https://help.ubuntu.com/community/Games/Native/QuakeIIIArena?highlight=%28quake%29](https://help.ubuntu.com/community/Games/Native/QuakeIIIArena?highlight=%28quake%29)

---

