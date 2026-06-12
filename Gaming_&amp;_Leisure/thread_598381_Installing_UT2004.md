---
title: "Installing UT2004?"
date: 2007-10-31
forum: Gaming &amp; Leisure
---

### Post by Vadi on 2007-10-31
I read a whole bunch of threads on this, but I even get stuck on the first step:

vadi@vadi-laptop:~/virtual-drives/1$ ls
AutoRun.inf  CD2  CD4  CD6       linux-installer.sh
CD1          CD3  CD5  DEViANCE  Setup.exe
vadi@vadi-laptop:~/virtual-drives/1$ sudo ./linux-installer.sh
sudo: ./linux-installer.sh: command not found


How do I go about this? :/

---

### Post by karth on 2007-10-31
is your installer script executable?

Try running ```
chmod +x linux-nstaller.sh
```
from inside the directory containing linux-installer.sh

then run```
./linux-installer.sh
```

You shouldn't need run via sudo in this case, since it installs everything into your user dir tree.

---

### Post by Vadi on 2007-10-31
Actually it says the root owns the file for some reason, not me.

This is all really weird:

```
vadi@vadi-laptop:~/virtual-drives/1$ ls
AutoRun.inf  CD2  CD4  CD6       linux-installer.sh
CD1          CD3  CD5  DEViANCE  Setup.exe
vadi@vadi-laptop:~/virtual-drives/1$ chmod +x linux-nstaller.sh
chmod: cannot access `linux-nstaller.sh': No such file or directory
vadi@vadi-laptop:~/virtual-drives/1$ sudo chmod +x linux-nstaller.sh
[sudo] password for vadi:
chmod: cannot access `linux-nstaller.sh': Permission denied
vadi@vadi-laptop:~/virtual-drives/1$ 

```

---

### Post by karth on 2007-10-31
You could run ```
ls -la
``` from inside your directory, in order to see exactly who owns what and why it still denies chmoding the file even through sudo...

---

### Post by Vadi on 2007-10-31
I think root just jacked my game:

```
vadi@vadi-laptop:~/virtual-drives/1$ ls -la
total 7247
dr-xr-xr-x  1 root root     2048 1970-01-01 01:00 .
drwxr-xr-x 10 vadi vadi     4096 2007-10-30 15:06 ..
-r--r--r--  1 root root       53 2004-03-04 02:47 AutoRun.inf
dr-xr-xr-x  1 root root     2048 2004-03-15 23:19 CD1
dr-xr-xr-x  1 root root     2048 2004-03-16 00:46 CD2
dr-xr-xr-x  1 root root     2048 2004-03-16 00:47 CD3
dr-xr-xr-x  1 root root     2048 2004-03-16 00:47 CD4
dr-xr-xr-x  1 root root     2048 2004-03-16 00:09 CD5
dr-xr-xr-x  1 root root     2048 2004-03-16 00:17 CD6
dr-xr-xr-x  1 root root     2048 2004-03-16 01:54 DEViANCE
-r--r--r--  1 root root 29627635 2004-03-04 10:42 linux-installer.sh
-r--r--r--  1 root root    24576 2004-03-04 02:57 Setup.exe
vadi@vadi-laptop:~/virtual-drives/1$ 

```

How can I get it back?

---

### Post by Cochise on 2007-10-31
open a terminal and type sudo nautilus /

then navigate to the folder with ut2004 select everything and right click on it and pick properties and change the owner to your username and the group to your username

---

### Post by karth on 2007-10-31
@Vadi: I just saw that you typed ```
sudo chmod +x linux-nstaller.sh
``` instead of ```
sudo chmod +x linux-installer.sh
```
Note the I of Installer was missing, that's why the command failed

---

### Post by Vadi on 2007-10-31
> **karth said:**
> @Vadi: I just saw that you typed ```
sudo chmod +x linux-nstaller.sh
``` instead of ```
sudo chmod +x linux-installer.sh
```
Note the I of Installer was missing, that's why the command failed

Hey well who made the typo in the first place! I only copy/pasted.

But that didn't work:

```
vadi@vadi-laptop:~/virtual-drives/1$ sudo chmod +x linux-installer.sh
[sudo] password for vadi:
chmod: cannot access `linux-installer.sh': Permission denied

```.

I'll try the nautilus option.

---

### Post by karth on 2007-10-31
My mistake, I apologize

The command line equivalent of the nautilus option is

```
sudo chown -R vadi:vadi ~/virtual-drives/1/*
```
You'll still have to flag your install script as executable.

Hope that helps.

---

### Post by Vadi on 2007-10-31
Ok it's really weird, Nautilus wasn't recognizing the folder "1" as a valid folder when it's run as root.

Same thing with Konqueror.

But if I run them not as root, it's fine..

---

