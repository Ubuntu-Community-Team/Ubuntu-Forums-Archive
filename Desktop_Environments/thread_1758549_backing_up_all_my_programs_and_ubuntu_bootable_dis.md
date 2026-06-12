---
title: "backing up all my programs and ubuntu bootable disk"
date: 2011-05-14
forum: Desktop Environments
---

### Post by wayne1980 on 2011-05-14
ok i am a bit of a noob at this so bare with me 

ok so i was wondering if there a program that i can use to back up all my programs and ubuntu to a boot able disk so say soming went wrong and i had to start over i could pop in the disk and reinstall with all my stuff ready is their a easy way of doing this if u need more info on wat i mean plz ask im new to this

thank u to all the ppl that take there time just to look if they can help me

---

### Post by lindsay7 on 2011-05-14
Read up on Clonezilla and Remastersys

---

### Post by wayne1980 on 2011-05-14
soooo their no easy way around this then??..and thank u 4 the info!

---

### Post by Megaptera on 2011-05-15
> **wayne1980 said:**
> soooo their no easy way around this then??..and thank u 4 the info!

Please think again ...
Remastersys is really easy and effective. A few clicks on GUI, wait for it to happen, then burn your CD/DVD ... couldn't be easier!!

Guide with screenshots
 [http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22/](http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22/)

---

### Post by wayne1980 on 2011-05-16
> **Megaptera said:**
> Please think again ...
Remastersys is really easy and effective. A few clicks on GUI, wait for it to happen, then burn your CD/DVD ... couldn't be easier!!

Guide with screenshots
 [http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22/](http://maketecheasier.com/backup-ubuntu-with-remastersys/2008/12/22/)


that is great info one problem tho :(

wayne@wayne-desktop:~$ gksu gedit /etc/apt/sources.list
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) remastersys/
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/wayne@wayne-deskremastersys/ttp://www.geekconnection.org/remastersys/repository  
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
wayne@wayne-desktop:~$ deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
wayne@wayne-desktop:~$ deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/sudo apt-get update
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
wayne@wayne-desktop:~$ sudo apt-get install remastersys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package remastersys
wayne@wayne-desktop:~$ 

any help plz..and thanks again

---

### Post by Megaptera on 2011-05-16
What version of Ubuntu are you using? For instance 11.04 (Natty) or 10.10 or 10.04 or .....

If Lucid (10.04) try the link at #3 here [http://ubuntuforums.org/showthread.php?t=1468782](http://ubuntuforums.org/showthread.php?t=1468782)

---

### Post by wayne1980 on 2011-05-17
> **Megaptera said:**
> What version of Ubuntu are you using? For instance 11.04 (Natty) or 10.10 or 10.04 or .....
 
If Lucid (10.04) try the link at #3 here [http://ubuntuforums.org/showthread.php?t=1468782](http://ubuntuforums.org/showthread.php?t=1468782)
 
 
sorry 4 late reply 10.04 i am using

---

