---
title: "New in Ubuntu"
date: 2009-01-03
forum: General Help
---

### Post by marcgh on 2009-01-03
A have noticed that when the title is New in Ubuntu many forum users will at least read it and try to help.

BUT

When I post a thread with a specific title :

[http://ubuntuforums.org/showthread.php?t=1029619](http://ubuntuforums.org/showthread.php?t=1029619)

after 3 hours in absolute beginners: 1 read (me)
after 1 hour in this forum: 1 read (also me)

Why is that?
Should I be less specific in the title?

When nobody reads the thread, surely I will get no help.

This time, thanks for reading

---

### Post by Ruyuk on 2009-01-03
Actually you should be more specific and on to the point your trying to get to if you want help.

---

### Post by marcgh on 2009-01-03
Thank you for your reply.
could I be more specific ?

[http://ubuntuforums.org/showthread.php?t=1029619](http://ubuntuforums.org/showthread.php?t=1029619)

---

### Post by marcgh on 2009-01-03
Thank you for your reply.
could I be more specific ?

[http://ubuntuforums.org/showthread.php?t=1029619](http://ubuntuforums.org/showthread.php?t=1029619)

---

### Post by xjgnsdof on 2009-01-03
You can't expect an answer within one hour at this forum. Titles should not only be concise and accurate, but should be attention-getting.

---

### Post by marcgh on 2009-01-03
Thank you for your reply.
could I be more specific ?

[http://ubuntuforums.org/showthread.php?t=1029619](http://ubuntuforums.org/showthread.php?t=1029619)

---

### Post by Ruyuk on 2009-01-03
Well in this other forums I am at gives you replies within a few minutes (normally like 2.)

---

### Post by Lung Men on 2009-01-03
have a PC with Windows Vista Premium on a 500 Gb Caviar SATA HDD and a 120 Gb Caviar SATA HDD which I used as back up storage before but no longer need since I added a 320 Gb USB External back up drive. 

I am planning to install Linux on the 120 Gb drive and configure the system for dual boot.  Since I have the extra drive, it would seem to me to make sense to have Windows and Linux on different drives to avoid the possibility of one OS conflicting with the other; but am not sure of the choices available and need some advice. Can anyone please answer the following questions.

1 - Do I have the choice of installing Windows and Linux on different drives or must they both be on the same drive in order to be able to boot from either OS at start up. 

2 - If they both have to be on the same drive, how should I partition the 500 Gb drive. My idea  would be to create a 400 Gb partition for Windows and to install Linux in the remaining partitioned space. I might even make the Linux partition much smaller since the bulk of my work files, music, photos, games etc would still be stored in my Windows partition. Any suggestions on this? 

3 - If they can be, and are installed on different drives, can we still refer to that configuration as dual boot . I suppose that, in this case, a screen still appears on start up to show the booting options available but each OS has its MBR., Bios Set-up and all that thecnical stuff on its own drive. I am searching the Net for articles on this subject.

3 - There are so many versions of Linux that the choice is difficult to make for a new comer like me. I am looking at Ubuntu after a bit of reading on the subject. Is this a good choice for someone who just wants to learn and experiment with it (But who knows. I might even possibly give up Windows eventually) 

4 - I came across some good articles and instructions on the Web about dual booting Windows/Linux but did not see anything specific about having these two OS’s on different drives in the same computer. If there are such articles, can anyone please point me to one of them.

I know this is a lot to ask but I was told that a very famous man once said “Ask and you will receive”

---

### Post by kokkus on 2009-01-03
If you need a quick reply u should post your msg in the general help forum, not in the noobies forum.
For some reason there are LOT more people here then in all the other forums.

---

### Post by albinootje on 2009-01-03
> **Lung Men said:**
> 
1 - Do I have the choice of installing Windows and Linux on different drives or must they both be on the same drive in order to be able to boot from either OS at start up. 

With Linux you have that choice.

Easiest would be to let Ubuntu write to the MBR of your main drive, but if you don't mind changing the BIOS every time, then choose to let it write to the disk where the / partition of Ubuntu during the Ubuntu installation will be created.

For example, if Windows is on /dev/sda, and you install Ubuntu on /dev/sdb1 (the / partition), with a swap partition on /dev/sdb2, then let it write the Grub bootloader to /dev/sdb

> 
3 - There are so many versions of Linux that the choice is difficult to make for a new comer like me. I am looking at Ubuntu after a bit of reading on the subject. Is this a good choice for someone who just wants to learn and experiment with it (But who knows. I might even possibly give up Windows eventually) 

Ubuntu is an excellent choice for a beginner, just like Fedora Linux, or OpenSUSE Linux or Mandriva Linux.

See also :
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Cope57 on 2009-01-03
**marcgh**, [look here...]("http://tinyurl.com/a8jtkq")

---

### Post by Lung Men on 2009-01-06
> **albinootje said:**
> With Linux you have that choice.

Easiest would be to let Ubuntu write to the MBR of your main drive, but if you don't mind changing the BIOS every time, then choose to let it write to the disk where the / partition of Ubuntu during the Ubuntu installation will be created.

For example, if Windows is on /dev/sda, and you install Ubuntu on /dev/sdb1 (the / partition), with a swap partition on /dev/sdb2, then let it write the Grub bootloader to /dev/sdb


Ubuntu is an excellent choice for a beginner, just like Fedora Linux, or OpenSUSE Linux or Mandriva Linux.

See also :
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Thanks for the reply and the 2 leads. 

At least now I know that what I want to do is possible and I will keep on reading and asking questions until I feel sure anough to make the move.

---

