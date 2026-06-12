---
title: "need help learning how to add new programs that I download"
date: 2005-09-03
forum: Desktop Environments
---

### Post by FreedomRider on 2005-09-03
yeah I'm having touble figuring out how to add stuff manually like a shockwave flash plugin for my browser and I also tried to install stuff like another irc client and when I download them and go to teminal or synaptic I can't load the programs 
I am a windows user and really want to use linux on one of my pc's 
but I am pulling my hair out 
 maybe someone can direct me to a guide or somewhere where I can get this moving lol
I am a total noob to linux but a well seasoned computer user otherwise
any help would be appreciated ](*,)

---

### Post by arnieboy on 2005-09-03
[QUOTE=FreedomRider]yeah I'm having touble figuring out how to add stuff manually like a shockwave flash plugin for my browser and I also tried to install stuff like another irc client and when I download them and go to teminal or synaptic I can't load the programs 
I am a windows user and really want to use linux on one of my pc's 
but I am pulling my hair out 
 maybe someone can direct me to a guide or somewhere where I can get this moving lol
I am a total noob to linux but a well seasoned computer user otherwise
any help would be appreciated ](*,)[/QUOTE]
read [http://ubuntuguide.org](http://ubuntuguide.org) . Most of your queries will get answered there. if u still dont understand something, ask specific questions and we will answer them.

---

### Post by Lambert on 2005-09-03
A couple good places to go and learn are...

[www.ubuntuguide.org](www.ubuntuguide.org)
[www.wiki.ubuntu.com](www.wiki.ubuntu.com)

there's a section in the forum called tips and tricks. Look for the post at top that says index.

You should be able to get what you need from these.

---

### Post by mcmuffy on 2005-09-03
If the program came in a .deb file use 
sudo dpkg -i filename.deb

If it is source code you would need to extract it with the archive program of your choice and then compile it. Usually instructions are in the archive but the general pattern is :

./configure
make
sudo make install

I think with flash you need to extract the archive and then type :
./flash-installer
or whatever the program is called.

---

