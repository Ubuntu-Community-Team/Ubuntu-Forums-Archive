---
title: "Installing Game with multiple discs"
date: 2006-12-16
forum: Gaming &amp; Leisure
---

### Post by underdog512 on 2006-12-16
I am trying to install Star trek Elite force 2 under Wine.  Problem is that there are 2 discs while setup is running, it ask me to insert the second disc. however the cd rom will not eject because it says that the device is busy.  what do I do?

---

### Post by Milos_SD on 2006-12-16
System -> Preferences -> Removable Drives and Media -> uncheck "Mount removable media when inserted". And when you instert CD in your CD ROM, go to Places -> Computer, and double click the CD Drive icon or whatever it is :) (this will mount that CD). When it says to instert second CD in the drive, just press the button on the CD drive to open it, and inster second CD. Then repeate the procedure for the firs CD (Places -> Computer -> double click the CD Drive to mount it).

P.S. Sorry for my bed english.

---

### Post by underdog512 on 2006-12-16
Thanks I will try that

---

### Post by unarmedninja on 2006-12-18
you can also type ```
wine eject
``` into the terminal and it will eject the disc for you. just make sure the next disc gets read before you click continue or the intaller might crash.

---

