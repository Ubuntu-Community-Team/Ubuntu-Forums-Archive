---
title: "installed compiz and it works, now how do i change settings?"
date: 2007-08-16
forum: Desktop Environments
---

### Post by Aesir09 on 2007-08-16
i have beryl and i liked, it so i decided to one day

```
sudo apt-get install compiz
```

worked great

so now i clicked on my beryl icon and select compiz as my window manager

works cool and i like the effects... but i dont have a settings manager!

---

### Post by merlyn on 2007-08-16
Install compizconfig-settings-manager with your preferred method.

---

### Post by Aesir09 on 2007-08-16
```
dom@ubuntu:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

```

---

### Post by merlyn on 2007-08-17
> **Aesir09 said:**
> ```
dom@ubuntu:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

```

Have you got the universe repositories enabled?  That's where the settings manger lives.

You can either edit your /etc/apt/sources list by entering the following in a terminal.```
sudo vi /etc/apt/sources.list
```Substitute vi with your preferred text editor.

Look for an entry that will appear similar to this,```
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
```Append "universe mulitverse" to the line, (without the quotes), so that it reads as such```
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
```While your at it do the same with any of the other Ubuntu repository entries.

Alternatively in synaptic just check the boxes in Synaptics "Software Sources" dialogue as per the attached screenshot. 

This can be launched from >settings>repositories .

Run an update via your normal method, then try to reinstall the CompizConfig Settings Manager again.

Cheers.

---

### Post by CameO73 on 2007-08-17
Better yet, just follow [this excellent guide](http://ubuntuforums.org/showthread.php?t=481314) to get the latest Compiz Fusion (= the next Compiz/Beryl). After installation you can find the configuration editor in System --> Preferences --> CompizConfig Settings Manager (no need for Beryl icon anymore!)

---

### Post by merlyn on 2007-08-17
Either will get you 0.5.2, as that is the version currently in the Gutsy repos.

---

