---
title: "Starting program with sudo at bootup?"
date: 2006-09-13
forum: Desktop Environments
---

### Post by DAFORZE on 2006-09-13
Hey guys!
I want to start 2 programs with sudo priviliges automatically when gnome starts. So i tried adding it to sessions -> startup programs, and added the lines:
- sudo xsupplicant -i eth0 -d 5 -f
- sudo dhclient eth0
But it doesn't seem to work, I have to enter it manually everytime I start ubuntu in a terminal to get my internet connection working..
Could anybody help me?
Thnx in advance!

---

### Post by Ramses de Norre on 2006-09-13
Do this:
```
echo "`whoami` ALL= NOPASSWD: /usr/bin/xsupplicant"|sudo tee -a /etc/sudoers
echo "`whoami` ALL= NOPASSWD: /sbin/dhclient"|sudo tee -a /etc/sudoers

```
Now the lines in startup programs should work.

EDIT: I don't have xsupplicant installed here so I can't test the path, type "which xsupplicant" to see it, if it's not /usr/bin/xsupplicant you should change it in the command.

---

### Post by yanqian on 2006-09-24
I have the similar problem, I installed xsupplicant by apt-get,and it automatically created a link in /etc/rc2.d,

$ ls -l /etc/rc2.d/ | grep xsupplicant
lrwxrwxrwx 1 root root 21 2006-09-10 23:26 S20xsupplicant -> ../init.d/xsupplicant

I think it should start at bootup, but it doesn't work, why?

I have to type the two commands everytime I start ubuntu:

$ sudo xsupplicant -i eth0 &
$ sudo dhclient &

then the network connection is OK.

---

