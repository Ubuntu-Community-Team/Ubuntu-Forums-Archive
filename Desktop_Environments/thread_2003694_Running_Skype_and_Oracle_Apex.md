---
title: "Running Skype and Oracle Apex"
date: 2012-06-14
forum: Desktop Environments
---

### Post by bencouve on 2012-06-14
Hi Guys, I need some advice. Was trying to dual boot my laptop but gave up and installed Ubuntu on an old PC which has pretty low spec. However, am very happy with using Ubuntu, even though it is running a bit slow. Have a Unix/Solaris background (some years ago now) so not surprising I am happy with Ubuntu really. 

Have Windows 7 running on laptop with Oracle Apex (the free version) and skype. I need both applications to be able to work properly. Am thinking of installing Ubuntu on my laptop and just running Linux. I do need Apex and Skype though.

Could you please comment on how Ubuntu runs with Skype and Apex and your general thoughts on my decision. Thanks in advance.

---

### Post by bencouve on 2012-06-16
Wow, I thought someone would have a comment to make on this. Is there nobody out there who has experienced running Apex or Skype on Ubuntu? I would be surprised if the answer is no to that question...

---

### Post by bencouve on 2012-06-21
Ok, since no one gave me advice on this I decided to go ahead with the ubuntu install anyway. Started with 32 bit, had no sound from speakers. Installed 64 bit and that problem went away. Skype works fine. Next project is to install Oracle Apex. That should be fun..

Will keep you updated ... since so many are interested ..:D

---

### Post by bencouve on 2012-06-26
It would appear Oracle is installed, mounted and running, but with a few errors.
The Oracle install was successfull but had to make changes to the partitions. See below.


sudo /etc/init.d/oracle-xe configure

In chapter 8

To resolve this I tried entering

mount -t tmpfs shmfs -o size=2048m /dev/shm

into file "/etc/init.d/oracle-shm"

as instructed in this url

[https://cn.forums.oracle.com/forums/...readID=2376116]("https://cn.forums.oracle.com/forums/thread.jspa?threadID=2376116")

However, that did not work either. So I tried creating a partition using
Gparted. This is also suggested in the above url. Here it is

shmfs            2097152   624088   1473064  30% /dev/shm

Note: so far have left the entry

mount -t tmpfs shmfs -o size=2048m /dev/shm

in /etc/init.d/oracle-shm

but may remove it later

This appears to have worked. I still got errors when running 
sudo /etc/init.d/oracle-xe configure but I can start the db. Will continue with this tomorrow as it is late.
One other thing, the url for apex or xe, does not work yet, this one

[http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex)

You may find this useful too. 

[http://mediakey.dk/~cc/howto-install-oracle-on-debian/]("http://mediakey.dk/%7Ecc/howto-install-oracle-on-debian/")

---

