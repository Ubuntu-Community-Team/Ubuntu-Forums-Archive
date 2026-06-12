---
title: "Increasing ubuntu's &quot;usage&quot; size."
date: 2009-03-14
forum: General Help
---

### Post by fm2h on 2009-03-14
I am new to the whole Ubuntu/Linux world. Recently I got my hands on the Ubuntu CD. I popped it in my DVD drive while logged on in my XP user account. What I got was "Wubi" (?). I typed in the user name, password, and the GB's to be used. At the time I only had a 40GB HDD. I gave 15GB to Ubuntu. Now I've updated my HDD to 250GB and wont to increase the total amount that ubuntu can use. Can someone walk me through it step by step, using the most simplistic language possible ?

I've tried to do it myself. I tried to look for the Ubuntu partition, which does not exist. It's some how inside one of the XP folders. If I go to "/host/ubuntu/disks" I see "extra.disk" that's using up 93.1GB. I see "new.disk" that's about 80GB, "root.disk" 13GB, "swap.disk" which is about 1GB. I know the root.disk is the main file, the swap.disk file is very important, too. What are the "extra.disk" and "new.disk" ? Can I delete them ? Are they the mistakes I made while trying the increase Ubuntu's usage ? 

One more thing. If I install Ubuntu on a partition can I still access my Windows XP files ? and If I install Ubuntu and it's own partition will it run faster ?

---

### Post by jerome1232 on 2009-03-14
The Wubi wiki has a how to on this. Baiscally your disks are virtual files system that are actually just large files on your Windows partition.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

### Post by fm2h on 2009-03-14
I've tried to use the website. It's too complicated. 

*You can use LVPM, at [http://lubi.sourceforge.net/lvpm.html*](http://lubi.sourceforge.net/lvpm.html*)

There are no instructions on how to use LVPM. I've used "resize" and got nothing. 



*As an alternative, you can use the following script to move /home or /usr to a dedicated virtual disk.*

Move /home and /usr/ ? What about the rest on the files ? Do I have to reinstall the other files ?


*Download wubi-add-virtual-disk, open a terminal and run:

sudo sh wubi-add-virtual-disk /home 15000

Where the first argument is the directory to move to a new dedicated disk, and the second argument is the size in MB.*

How do I transfer all my data to the new directory ?

*The 2 directories you are most likely to migrate are /home (if you have a lot of user data) and /usr (if you installed a lot of software).*

How do I "mirgrate" ?

---

