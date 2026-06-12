---
title: "Ubuntuu partition resizing"
date: 2008-11-20
forum: Desktop Environments
---

### Post by Galva on 2008-11-20
Hello there. Im wery new to ubuntu - just instaled it yesterday as second OS. Main is XP.
I have problem with hdd space.
I have 3 HDD
1. 80gb  - there is XP
2. 500gb - random stuff
3. 500gb - yust bought and tryed to instal ubuntu
So I created several partitions o last (3.) hdd with xp help, then I tryed to instal ubuntu. when it has ended to install on 3. hdd, there was no more many partitions, just one big ubuntu over all 500gb, I wanted to resize it so I can instal also Vista on the 3. hdd and maybe some more OS. How to resize it?
There was one partition program on ubuntu but it dosnt alow me to resize the 3.hdd.
Hope that someone will help!
Thanks.
Kristaps

---

### Post by mitchroberts on 2008-11-21
never tryed this before but this program is free

[http://partitionlogic.org.uk/](http://partitionlogic.org.uk/)

"got ubuntu"

---

### Post by shcaesar on 2008-11-21
If only a ubuntu program can satisfy you, you can try gparted (Just open a terminal, and type gparted).

However, if you use the ubuntu system on your HD, you cannot resize the partition for /; in this case, boot up with your live CD (the CD you used for installation is a live CD), then use gparted to resize.

gparted is very easy to use. So good luck!

---

### Post by Galva on 2008-11-23
OK!
I will try when I will remove already used space from HDD :)

---

### Post by caljohnsmith on 2008-11-23
Just an FYI, but if you run gparted from the command line, you have to run it as root:
```
gksudo gparted
```
If you boot your Live CD, you can also access gparted by going to System > Admin > Partition Editor. Good luck and let us know how it goes. :)

---

