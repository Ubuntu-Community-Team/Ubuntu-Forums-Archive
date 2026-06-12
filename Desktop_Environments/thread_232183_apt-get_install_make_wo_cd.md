---
title: "apt-get install make w/o cd"
date: 2006-08-08
forum: Desktop Environments
---

### Post by yargevad on 2006-08-08
the title pretty much says it all... how can i force apt-get to download a package instead of prompting for the cd to be inserted?

---

### Post by Ronbo on 2006-08-08
In a terminal open up your /etc/apt/sources.list file with gedit using sudo.

    sudo gedit /etc/apt/sources.list

Comment out this line by putting a '#' in front of it.

    deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


Save the file and do an apt-get update, then you will no longer need the CD when installing software via Synaptic or apt-get.

---

### Post by yargevad on 2006-08-08
Aha! Thanks for the tip, dunno how i missed that :-P

---

