---
title: "Unable to Mount Drive using SSHFS.. It used to work before"
date: 2016-07-28
forum: Desktop Environments
---

### Post by ramsforums on 2016-07-28
I have a VPS Hosted website. I used to mount directly on my Linux laptop and it was working. Past 3 months I never used and suddenly when I tried today it is not working.

I used to use the following command to mount

Code:
```
 sudo sshfs -o idmap=user root@1x8.2xx.78.x3:/  /mnt/netdrive
```
upon issuing the above command, password prompt appears and it gets authenticated. But when Iaccess drive I get error

See the screen short


[IMG]http://i.imgur.com/9kRnJPO.png[/IMG]



```
robert@develop /mnt$ cd /mnt
robert@develop /mnt$ sudo ls -l
[sudo] password for robert: 
total 4
drwxr-xr-x 1 root 500 4096 May 23  2015 netdrive

```

if I try

```

ssh root@1x8.2xx.78.x3

```
It works fine.

May I request yourhelp. Why I am unable to mount?


Thanks

---

### Post by mikey93898 on 2016-07-31
Try the -o debug option and see if it says anything useful

---

