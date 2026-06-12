---
title: "Can't install programs that I need."
date: 2008-12-06
forum: General Help
---

### Post by nick09 on 2008-12-06
```

nick@family-pc:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ia32-libs lib32asound2 lib32gcc1 lib32ncurses5 lib32nss-mdns lib32stdc++6
  lib32z1 libc6-i386 nspluginwrapper
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree ia32-libs lib32asound2 lib32gcc1 lib32ncurses5
  lib32nss-mdns lib32stdc++6 lib32z1 libc6-i386 nspluginwrapper
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

Thanks for any help.

---

### Post by eBoxNet on 2008-12-06
try this : sudo pkill apt and then try to install your progs.
alse check if you run any other package manager or updater and if yes close them.

---

### Post by dexter on 2008-12-06
There can only be one instance of the packet manager active. For instance you can not use apt-get when synaptic is running or vice versa. This is what the error message is telling: another instance is currently using /var/cache/apt/archives/lock. Wait for its' completion, close it and retry installing your software. 

If you didn't open synaptic, it could also have been the automatic update manager.

---

### Post by nick09 on 2008-12-06
I tried that and it did not work. I also am not running any updates or anything either. I do notice there is a file named lock. Anyway I can fix it?

---

### Post by fooman on 2008-12-06
try one/all of these (try the first,  see if it fixes,  if not then try the next,  etc..):

```
sudo killall synaptic
sudo killall apt-get
sudo killall dpkg
```

---

### Post by nick09 on 2008-12-06
They all say that the process is not killed:
```
nick@family-pc:~$ sudo killall synaptic
synaptic: no process killed
nick@family-pc:~$ sudo killall apt-get
apt-get: no process killed
nick@family-pc:~$ 
nick@family-pc:~$ sudo killall dpkg
dpkg: no process killed
nick@family-pc:~$ 

```

---

### Post by fooman on 2008-12-06
give this a shot:

```
sudo rm /var/cache/apt/archives/lock
```

---

### Post by nick09 on 2008-12-06
Thank you for the help.

---

