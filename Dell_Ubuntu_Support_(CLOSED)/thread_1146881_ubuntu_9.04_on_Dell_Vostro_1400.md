---
title: "ubuntu 9.04 on Dell Vostro 1400"
date: 2009-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by babloo75 on 2009-05-03
I want to install Ubuntu 9.04 on Dell Vostro 1400 with 160 GB HD which has Windows Vista preinstalled on it. want to have a dual boot on the system. Is there any pictorial illustration of the same on internet. I have little knowledge of HD partitions, so cannot do it with manual partitions. tried it with automatic method but this method was giving only 2.5 GB of space to Ubuntu 9.04. So aborted the installation and have come here to ask this question. 
One more thing I have noticed that unlike 8.10 version this new Ubuntu 9.04 does not have a slider for modifying the partitions of HD while installation.. Don't understand why Ubuntu staff has made this task difficult for the inexperienced ones. May be they want to do the same thing what MS windows has done from XP to Vista, decreasing the number of users so that less number of people use Ubuntu and shift to some other OS, anyway this is not a place to discuss such issues. 
Let me come to the topic once again. I need your help to install Ubuntu 9.04 on Dell Vostro 1400. 
One more thing I tried Ubuntu 8.10 on this laptop earlier but have experienced a strange thing, while i tried the slider for partitioning the HD to make it dual boot, it showed me that after final installation whole of the hard disk will be occupied with Ubuntu, which I don't want. So had to quit this installation in between and had to format the HD and re install Vista on it. Thats why I don't want to install 8.10 and later upgrade it.
Please tell me a simple method (with pictorial illustrations) to install Ubuntu 9.04 on this laptop.
Thanks in advance.

---

### Post by panmoto on 2009-05-03
this may help you :
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

yes, it's not specific about ubuntu, but at least it will give you some insight.

---

### Post by superm1 on 2009-05-03
> **babloo75 said:**
> I want to install Ubuntu 9.04 on Dell Vostro 1400 with 160 GB HD which has Windows Vista preinstalled on it. want to have a dual boot on the system. Is there any pictorial illustration of the same on internet. I have little knowledge of HD partitions, so cannot do it with manual partitions. tried it with automatic method but this method was giving only 2.5 GB of space to Ubuntu 9.04. So aborted the installation and have come here to ask this question. 
One more thing I have noticed that unlike 8.10 version this new Ubuntu 9.04 does not have a slider for modifying the partitions of HD while installation.. Don't understand why Ubuntu staff has made this task difficult for the inexperienced ones. May be they want to do the same thing what MS windows has done from XP to Vista, decreasing the number of users so that less number of people use Ubuntu and shift to some other OS, anyway this is not a place to discuss such issues. 
Let me come to the topic once again. I need your help to install Ubuntu 9.04 on Dell Vostro 1400. 
One more thing I tried Ubuntu 8.10 on this laptop earlier but have experienced a strange thing, while i tried the slider for partitioning the HD to make it dual boot, it showed me that after final installation whole of the hard disk will be occupied with Ubuntu, which I don't want. So had to quit this installation in between and had to format the HD and re install Vista on it. Thats why I don't want to install 8.10 and later upgrade it.
Please tell me a simple method (with pictorial illustrations) to install Ubuntu 9.04 on this laptop.
Thanks in advance.
If you aren't getting the slider when you try to install, that generally means one of thee things:

1) You improperly shutdown windows before booting the Ubuntu CD
2) Your current windows partition is flagged dirty.  You can schedule a disk check in windows for it.  Once it runs, cleanly shutdown or reboot
3) You don't have enough free space on the windows drive.  Make sure you've got enough.

Something else I'd recommend is perhaps just installing with Wubi.  It lets you install the OS as a file on the windows partition rather than resizing the disk.

---

### Post by babloo75 on 2009-05-06
Thanks

---

