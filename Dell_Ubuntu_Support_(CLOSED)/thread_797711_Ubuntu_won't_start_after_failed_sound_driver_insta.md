---
title: "Ubuntu won't start after failed sound driver install"
date: 2008-05-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Cubibubi on 2008-05-17
Hello,

yesterday I finally tried to install some drivers for my sound card, the Creative Soundblaster X-Fi. Although I hadn't had everything configured right and didn't have all packages I needed and didn't have all configured kernels and ALSAs (I'm new to Linux), I typed ./configure and sudo make. That worked somehow. 
Without expecting the next command to work, I typed sudo make install. (Well I knew and now i know even more that that was very stupid, please don't tell me that.)

Then Ubuntu gradually freezed and I had to hardcore restart my PC (with the LED button = actually by turning off the power).

From then, everytime i start Ubuntu it loads until it has to load the sounddrivers. I tried rescue mode, and it convinced me that it stops at the sounddrivers.


Now my question is: How can I disable/deinstall/turn-off-when-starting-up my sound drivers via command line (in the rescue mode)?


Thank you VERY MUCH in advance!


EDIT: Now that I installed a piece of software letting me access my Linux harddrive from Windows, I can also manually delete certain driver files, so this kind of help would be appreciated as well!

---

### Post by shvahabi on 2009-01-06
Hi dear,

MINE is DELL Inspiron 6400, running Ubuntu 8.10

I had the same problem. Actually I couldn't solve it, but there is a way to access your hard drive. At least I did succeded.

1. insert the CD-ROM from which you installed Ubuntu.
2. use the first item, i.e. try Ubuntu without any change to your system.
3. stand by for system to completely boot up
4. your inacessible hard drive will be available through PLACES at the main panel (2nd item from left on the bar to the top of the desktop)
5. you should mount it by clicking on its icon

I don't know why the hell everybody can access my hard by inserting installation CD into drive :confused:. But I think they should fix such a huge security issue on their OS. Surprisingly this issue is on your side, so get pleased :D

Don't forget to backup previously installed packages by:

```
gksu nautilus /var/cache/apt/archives
```

this is where Ubuntu saves Synaptic package manager downloads to hard. After backing up your data, if you installed Ubunt again, just copy the contents of the opened window to the same directory of newly installed Ubuntu

Shahed Vahabi
From Iran

---

