---
title: "Help!!!! Seirous Problem"
date: 2006-02-01
forum: Desktop Environments
---

### Post by shade11 on 2006-02-01
I posted this question before but I got no reply I need an answer or else I cant use Ubuntu.

After trying to install Firefox 1.5 from the wiki instrutions I cant loginin after x. Nor can I boot into failsafe. Please help!!!!!! I cant do anything. Even Ubuntu on antoher partition wont login. It says somethoing about shorter than 10 seconds and about small hard disk space, but I have aot of space!!

I need help. I have to do so many things on my PC. I have to get this fixed!!! Please HELP!!!!

Also it shows this when typing df -h

/dev/sda4 5.6G 4.9G 420M 93% /
tmpfs 253M 0 253M 0% /dev/shm
tmpfs 253M 13M 240M 5% /lib/modules/2.6.12-10-386/volatile
/dev/sda1 63M 7.2M 56M 12% /media/sda1
3.4G 3.0G 3999M 89% /media/sda3

When I use gParted on a Live disk it says it is there and it shows that the partition is there and it seems to be normal. . .

What do I do?!?!?!?

---

### Post by ipp3l1 on 2006-02-01
Does this help :

When in login screen, choose "failsafe terminal" as a booting option and run it with your account. Then, insert this code :

```
sudo chown johndoe /home/johndoe/.ICEauthority
sudo chmod 600 johndoe /home/johndoe/.ICEauthority
```

johndoe=your login name (naturally)

Or simply just remove the .ICEauthority file. Then reboot an should be workin \\:D/

---

### Post by shade11 on 2006-02-01
THANK YOU! I can not thank you enough.

THANKS!!!

---

### Post by Lord Illidan on 2006-02-01
[quote=shade11]I posted this question before but I got no reply I need an answer or else I cant use Ubuntu.

After trying to install Firefox 1.5 from the wiki instrutions I cant loginin after x. Nor can I boot into failsafe. Please help!!!!!! I cant do anything. Even Ubuntu on antoher partition wont login. It says somethoing about shorter than 10 seconds and about small hard disk space, but I have aot of space!!

I need help. I have to do so many things on my PC. I have to get this fixed!!! Please HELP!!!!

Also it shows this when typing df -h

/dev/sda4 5.6G 4.9G 420M 93% /
tmpfs 253M 0 253M 0% /dev/shm
tmpfs 253M 13M 240M 5% /lib/modules/2.6.12-10-386/volatile
/dev/sda1 63M 7.2M 56M 12% /media/sda1
3.4G 3.0G 3999M 89% /media/sda3

When I use gParted on a Live disk it says it is there and it shows that the partition is there and it seems to be normal. . .

What do I do?!?!?!?[/quote]

Do you call 420M left on your / partition a lot of space??

---

### Post by LanceM on 2006-02-01
It seems like this is happening more frequently.

---

### Post by ipp3l1 on 2006-02-01
Yes. Apparently, when ppl install some KDE applications, the .ICEauthority file's owner changes and causes problems... It same happened to me too:-k

---

### Post by shade11 on 2006-02-01
[QUOTE=Lord Illidan]Do you call 420M left on your / partition a lot of space??[/QUOTE]

It was another partition.

Who cares I have the problem fixed.

---

