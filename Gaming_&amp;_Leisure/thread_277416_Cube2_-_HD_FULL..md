---
title: "Cube2 - HD FULL."
date: 2006-10-14
forum: Gaming &amp; Leisure
---

### Post by kelmer on 2006-10-14
HI EVERYONE,
I installed Cube 2 this afternoon and after 30 min playing, I,ve received a message saying that my HD was 98% full. And in fact it was. So, I presume the game is storing something on my system, but I have no idea why and where. So the pc is quite sluggish now and I want to find out how to delete this files and fix the problem. Anyone ?

Thanks in advance.

---

### Post by ZylGadis on 2006-10-14
man du

du stands for disk usage, and will tell you the space occupied by directories. So

du -sh

will tell you the space occupied by the current dir, while

du -sh /*

will tell you the space occupied by each dir one level below the root. You can go from there and find the place where cube stores its things. (it is more than likely somewhere in /tmp)

Hope that helps.

---

### Post by JAwuku on 2006-10-14
To clear the old .deb files which tend to accumulate with downloads and updates, you can run the command:
```
sudo apt-get clean
```

then type ```
df-h
```

to get the amount of space on disk.

---

### Post by kelmer on 2006-10-15
Hi there,

thanks a lot for your help guys, I've finaly identified the problem. the game was generating a massive error log file at /var/log/syslog.0 about my graphic card, and reached a point in which I couldn't log in any more (100% hd), so I logged in in safe mode and removed this file (I tried editing the file with vim but didn't work). I hope this file is not important for anything else.

Thanks again...

---

