---
title: "Star Wars Jedi Knight II: Jedi Outcast Linux Native"
date: 2015-05-16
forum: Gaming &amp; Leisure
---

### Post by garyzw on 2015-05-16
How to install the Linux native port of Star Wars Jedi Knight II: Jedi Outcast.

Install the needed libraries for 64 bit:
```
sudo apt-get install libopenal1:i386
sudo apt-get install libx11-6:i386
sudo apt-get install libxxf86vm1:i386
sudo apt-get install libxrandr2:i386
sudo apt-get install libsdl1.2debian:i386
```

Download the 1.04 Update:

[http://help.starwars.com/articles/en_US/FAQ/Where-do-I-find-the-latest-patch-for-Jedi-Knight-II-Jedi-Outcast?section=Star-Wars](http://help.starwars.com/articles/en_US/FAQ/Where-do-I-find-the-latest-patch-for-Jedi-Knight-II-Jedi-Outcast?section=Star-Wars)


Clone the git repo:

git clone git://github.com/xLAva/JediOutcastLinux.*git

Install Star Wars Jedi Knight II: Jedi Outcast using WINE:

cd YOURCDMOUNTPOINT/Install/
wine Launch.exe

Install the 1.04 update:

wine JKIIUp104.exe

Copy the *.pk3 files from the WINE install:


Locate the base directory in "~/.wine/drive_c/Program Files/LucasArts/Star Wars JK II Jedi Outcast/GameData/"


Copy base directory into the "~/Desktop/JediOutcastLinux/code/Release folder"


Run the game:


Launch the game with ./jk2sp located in "~/Desktop/JediOutcastLinux/code/Release folder"

---

### Post by aramil248 on 2015-05-24
good guide but wont it be easier just to download the binaries off of jkhub? link: [http://jkhub.org/files/file/2263-jedi-outcast-sp-linux-binaries/](http://jkhub.org/files/file/2263-jedi-outcast-sp-linux-binaries/)

---

### Post by garyzw on 2015-05-24
> **aramil248 said:**
> good guide but wont it be easier just to download the binaries off of jkhub? link: [http://jkhub.org/files/file/2263-jedi-outcast-sp-linux-binaries/](http://jkhub.org/files/file/2263-jedi-outcast-sp-linux-binaries/)

Yes it would. I didn't know about binaries

---

### Post by aramil248 on 2015-05-24
i didn't know ether i usually compile them thats what i do for jedi academy.

---

### Post by Francesco_Verlato on 2015-05-28
Thank you i love this saga ):P

---

