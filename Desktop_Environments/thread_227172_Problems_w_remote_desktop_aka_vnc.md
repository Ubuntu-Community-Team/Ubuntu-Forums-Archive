---
title: "Problems w/ remote desktop aka vnc"
date: 2006-08-01
forum: Desktop Environments
---

### Post by srikat on 2006-08-01
I want to connect to my home machine running ubuntu from office (Windows XP). 

I followed [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC) and set it up w/ a password.

Now when I type vncserver in the terminal to start it, get:

```
sri@sridhareena:~$ sudo vncserver
vncserver: Wrong type or access mode of /home/sri/.vnc.
```

I tried tightvnc and get the same thing.

did "sudo chmod 700 /home/sri/.vnc" but no change.

Any ideas?

---

