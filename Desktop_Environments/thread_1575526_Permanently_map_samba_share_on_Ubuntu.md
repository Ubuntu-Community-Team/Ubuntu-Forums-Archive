---
title: "Permanently map samba share on Ubuntu"
date: 2010-09-15
forum: Desktop Environments
---

### Post by CorvetteFan86 on 2010-09-15
This is driving me crazy trying to figure this out. I am running ubuntu server 9 and I'm trying to permanently map the share to a users desktop (Using Ubuntu 8.04 - its a slow system). I am able to successfully mount it but once the user reboots it goes away. Any help would be greatly appreciated. 

Thanks,
Thomas

---

### Post by 3rdalbum on 2010-09-15
You need to add it to /etc/fstab so it is mounted on bootup. I'll admit that I can't walk you through this without looking at a HOWTO (been a few years since I've touched /etc/fstab) but there should be some HOWTOs online to help you; if not, then maybe someone else here will be familiar with the process and can walk you through.

---

### Post by CharlesA on 2010-09-15
It's a bit more complicated then mounting a regular drive, but you can find some info [here]("http://ubuntuforums.org/showthread.php?t=288534").

---

### Post by CorvetteFan86 on 2010-09-22
Thanks for the information CharlesA. I followed the link you mentioned and got the drive to map in no time!

---

### Post by CharlesA on 2010-09-22
Glad it's working. Don't forget to mark the thread as solved. :)

---

