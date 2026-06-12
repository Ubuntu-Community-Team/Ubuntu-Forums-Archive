---
title: "enable crashdump/diskdump &amp; crashdump=1"
date: 2009-05-31
forum: General Help
---

### Post by evuraan on 2009-05-31
I've a system which goes numb at times, even hangcheck-timer does not help. 

(1) How do we enable crashdump/diskdump on ubuntu? 

```

$ last |grep crash
user2 tty7         :0               Sun May 31 14:07 - crash  (00:02)    
user2 tty7         :0               Sat May 30 23:31 - crash  (14:36)    
user1      pts/0         Sun May 24 12:22 - crash  (09:14)    
user2 tty7         :0               Sun May 24 01:07 - crash  (20:29)    
user2 tty7         :0               Sat May 23 16:56 - crash  (08:11)    
user2 tty7         :0               Fri May  8 20:47 - crash (3+16:29)   
user2 tty7         :0               Tue May  5 06:53 - crash (3+13:53)   

```

(2) /boot/grub/menu.lst has 
```
## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

```

What would setting crashdump=1 do? 

```

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy

``` 

many thanks in advance..!

---

### Post by evuraan on 2009-06-01
I think there is no such thing as a diskdump capture yet in ubuntu - more [here]("https://bugs.launchpad.net/ubuntu/+bug/157777/comments/66").

[https://bugs.launchpad.net/ubuntu/+bug/157777/comments/66](https://bugs.launchpad.net/ubuntu/+bug/157777/comments/66)

oh well.

---

