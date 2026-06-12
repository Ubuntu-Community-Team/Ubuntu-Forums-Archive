---
title: "Gaim Crashes  and  Repartitioning HD"
date: 2006-07-17
forum: Desktop Environments
---

### Post by turok on 2006-07-17
Hi,i'm having some troubles with gaim. I start it and log in, and every thing goes fine, it loads the contact list and then it crashes, it closes itself. I thought maybe these could be becouse of my internet conection (i've been having some troubles with it lately, and web browsing has become very slow, despite my download rates are acceptable, pretty strange). btw i'm using xgl+compiz
Any ideas of what to do to solve this ?

Apart from that i have an ntfs partition in my drive and i want to format it  in order to use it with linux. I've tried with cfdisk but it says "FATAL ERROR: Cannot get disk size"  i type "sudo cfdisk /media/sda6" is that ok ?
How can i do it ?

Thanks a lot

---

### Post by Paerez on 2006-07-17
I dunno about gaim, but the partitioning should not be given a partiton, it should be given a disk:
```
sudo cfdisk /media/sda
```

---

### Post by turok on 2006-07-18
Thanks for you reply ! I tried doing what you said but i got the same error message. it's really strange.

---

### Post by Madarco on 2006-07-18
I've installed Dapper 6.06 in a new partition and I have the same problem, gaim goes segfault after few seconds. I'm using a msn and a irc account. Any suggestion?
Thanks.

---

### Post by Nicolae on 2006-07-18
For the partitioning, wouldn't you need to use "/dev/sda" and not "/media/sda"?

---

### Post by Paerez on 2006-07-18
uh yes. Yes you would. Let this be a lesson to all of you. Don't drink and post.

---

