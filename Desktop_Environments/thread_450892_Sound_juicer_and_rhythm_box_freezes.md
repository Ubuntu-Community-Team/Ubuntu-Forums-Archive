---
title: "Sound juicer and rhythm box freezes"
date: 2007-05-21
forum: Desktop Environments
---

### Post by brotell on 2007-05-21
Sound juicer and rhythm box freezes when i put a disk into my drive.  The same drive uses dvd's and there is no problem. The only changes I have made is updating my operating system UBUNTU EDGY EFT using the software updates as they become available. I have also added AVG virus checker. Can anyone suggest an answer to this problem. I had the same problem a while ago and become so frustrated that I reloaded Ubuntu before the updates and adding AVG the was no problem.

Ta Terry

---

### Post by mitch.c on 2007-05-23
Does Soundjuicer and rhythmbox freeze, or does you system freeze? If it's you whole system (which happened to me), it may be caused cdparanoia. I had to go back to a previous version to solve the problem.
```
$ sudo apt-get install cdparanoia=3a9.8-13 libcdparanoia=3a9.8-13
```
Launchpad Bug: [https://bugs.launchpad.net/ubuntu/+source/cdparanoia/+bug/106000](https://bugs.launchpad.net/ubuntu/+source/cdparanoia/+bug/106000)

---

### Post by brotell on 2007-05-29
Mitch I tried your solution but all I get is 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '3a9.8-13' for 'libcdparanoia' was not found
does this mean I have to delete current cdparanoia before I can apt get the earlier version..
Terry

---

### Post by mitch.c on 2007-05-29
> **brotell said:**
> Mitch I tried your solution but all I get is 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '3a9.8-13' for 'libcdparanoia' was not found
does this mean I have to delete current cdparanoia before I can apt get the earlier version..
Terry
Sorry, my mistake:
```
sudo apt-get install libcdparanoia0=3a9.8-13
```
That should do it.

---

### Post by mitch.c on 2007-05-29
I should also point out that you are going to want to 'hold' these packages at the specified version, otherwise, they'll get upgraded automatically. There are two ways (that I know of) you can do this:

Using Aptitude:
```
$ sudo aptitude hold cdparanoia libcdparanoia0
```
Using dpkg:
```
$ sudo bash -c "echo libcdparanoia0 hold | dpkg --set-selections"
$ sudo bash -c "echo cdparanoia hold | dpkg --set-selections"
```
The downside here is that your update-notifier is always going to tell you to update. I think there is a way to avoid that by "pinning" the packages in /etc/apt/preferences, but I haven't had time to check.

---

### Post by brotell on 2007-05-29
Mitch your a life saver did what you suggested and it works a treat.
Thank you again.
As a newbie I am learning and thanks to you I have learned more.

Regards

Terry

---

