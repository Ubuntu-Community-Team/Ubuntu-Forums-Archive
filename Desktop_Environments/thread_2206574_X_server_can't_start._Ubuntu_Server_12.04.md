---
title: "X server can't start. Ubuntu Server 12.04"
date: 2014-02-19
forum: Desktop Environments
---

### Post by Ptomerty on 2014-02-19
After installing X11 on my Ubuntu Server 12.04.4 LTS using this guide:
[http://hashcat.net/wiki/doku.php?id=linux_server_howto](http://hashcat.net/wiki/doku.php?id=linux_server_howto)
It never starts up.
I have an AMD Radeon 7950, and it is detected if I run ```
sudo aticonfig --lsa
```, but if i run ```
sudo aticonfig --adapter=all --odgt
``` it gives me the error ```
ERROR: X needs to be running to perform AMD Overdrive(TM) commands.
```
In my .bashrc file, export DISPLAY=:0 is at the very end, however it doesn't seem to be taking effect.
If I want a program to recognize my GPU, i have to run ```
DISPLAY=:0 sudo <command>
```, which I don't want to do because of security issues.
Can anyone help?

---

### Post by Ptomerty on 2014-02-20
bump, losing my mind, nothing i can do gets export DISPLAY=:0 to run.

---

### Post by deadflowr on 2014-02-21
What happens if you run
```
startx
```
?

---

