---
title: "How to specify apt-get sources?"
date: 2005-07-08
forum: Desktop Environments
---

### Post by fresco on 2005-07-08
I just installed Ubuntu from ISO image on my harddisk. 
When I install some applications like mplayer there is message from apt:

Media change: please insert the disc labeled
'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter

Well, I don't have that cd, only an iso file.   :grin: How can I tell apt to download all the files from the network without using cd?

Thanks form any help!  ;-)

---

### Post by PMO6022 on 2005-07-08
Edit the file /etc/apt/sources.list and comment out the line that refers to the cd, usually the first line.  

You will also need to setup the network sources in that file if they are not already there.  See [www.ubuntuguide.org]("http://www.ubuntuguide.org") for more info on that.  After the file is edited, run: **sudo apt-get update** and you should be good to go.

---

### Post by maruchan on 2005-07-08
More specifically, do what it says here:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by trash on 2005-07-08
Hey there, congrats and enjoy:)

Most questions you will have during setup will be answered here in the starter guide.

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

etc/apt/sources.list is the file you will want to modify and you can do it by using:

sudo gedit /etc/apt/sources.list

you'll find the rest of the info in the starter guide.

good luck:)

---

### Post by fresco on 2005-07-08
Thank you all for help! Several answers in a few minutes!  WOW! God bless this community!  O:)

---

### Post by maruchan on 2005-07-08
Ooh! I forgot something...you will want to edit that sources.list file and change all occurrences of "us.archive.ubuntu.org" to just "archive.ubuntu.org" or you will have problems. At least, I had problems. I found that solution here on the forum.

---

