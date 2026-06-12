---
title: "Problem installing Bluefish w/ apt-get"
date: 2005-06-26
forum: Desktop Environments
---

### Post by viking956 on 2005-06-26
Hello

I'm trying to install Bluefish and getting a prompt to insert the Hoary CDROM(see below), which I don't have. Is there any way around this?
Thanks!

Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter

---

### Post by Xian on 2005-06-26
You just need to open your sources.list and comment the line that begins with "deb cdrom". Then save the file and Apt will not look for that media while installing packages.

```
$ sudo gedit /etc/apt/sources.list
```
Modify the cdrom line to look like this:
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
```

---

### Post by viking956 on 2005-06-26
That did it,
Thanks a lot!

---

### Post by pixelnate on 2005-07-12
Sorry to ask a stupid question, but how exactly can I get Bluefish? I really have tried following all instructions I can find on the net. It goes something like this:

pixelnate@silverbuntu:~$ sudo apt-get install bluefish
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package bluefish
pixelnate@silverbuntu:~$

What am I doing wrong here. I just don't understand the ins and outs of apt-get. Thanks in advance.

-pixelnate

---

