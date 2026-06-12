---
title: "Installing Ubuntu-Desktop 14.04.03(LTS) alongside Kubuntu 15.04"
date: 2015-09-11
forum: Desktop Environments
---

### Post by alexel2 on 2015-09-11
Hi, I'm wondering if it's possible to do the above stated. I am aware using apt-get install ubuntu-desktop works, using a chosen dm. However; this automatically installs the non-LTS version of Ubuntu-Gnome, which is still somewhat unstable. I've learned this the hard way. Can I use the 14.04 ubuntu desktop along Kubuntu 15.04, or is it impossible due to the core files?  If it is possible, what is the least complicated method to do it - and for future reference obliterating one version from the other side? It goes without saying I'm new. Help would be very much appreciated, thank you!

---

### Post by Bucky Ball on 2015-09-11
Welcome. ubuntu-desktop installs a lot more than just that version of Gnome. It installs ALL default software related to Ubuntu and you are, in effect, whacking a full Ubuntu install on top of Kubuntu. Definitely NOT the way to go.

If you just want the desktop environment, just install Unity. 

```
sudo apt-get install unity
```

... or look in whatever package manager Kubuntu uses and install from there. Log out, choose the Unity desktop from the Sessions menu, log in.

---

### Post by howefield on 2015-09-11
> **alexel2 said:**
> Hi, I'm wondering if it's possible to do the above stated.

Yes, it's possible. Although you can install Unity as opposed to the full blown ubuntu-desktop packages.

> Can I use the 14.04 ubuntu desktop along Kubuntu 15.04, or is it impossible due to the core files?  If it is possible, what is the least complicated method to do it - and for future reference obliterating one version from the other side? It goes without saying I'm new. Help would be very much appreciated, thank you!

A dual booting machine seems to be what you want with Kubuntu and Ubuntu each having separate partitions on your hard disk, the least complicated way for someone new ? Give the machine to someone else and get them to do it for you.

Before you start ensure that all important data is safely backed up so that your next thread will not be of the "how to recover data" kind. 

If it were mine, I'd image the drive with Clonezilla to give a way back to the starting point then partition the disk making space for Ubuntu and install into it. How large is your disk and what is currently on it ?

---

### Post by CantankRus on 2015-09-11
If you wanted ubuntu-desktop 14.04.03(LTS) as well Kubuntu 15.04, you would have to create and install to a different partition.
[COLOR="#FF0000"]**Edit:**[/COLOR] see above post

---

### Post by grahammechanical on 2015-09-11
> [COLOR=#000000]Can I use the 14.04 ubuntu desktop along Kubuntu 15.04, or is it impossible due to the core files? [/COLOR]

Each version of Ubuntu has its own repositories that are used by Ubuntu and the flavours. If you put the URL to the main trusty (15.04) repository into the list of software sources for a vivid (15.04) system you will most definitely get errors when you update. If we use 15.04 and install an alternative desktop we get the appropriate software from the 15.04 repositories.

I do not agree that that Ubuntu 15.04 is somewhat unstable. I am using Ubuntu 15.10 and that is fantastically stable and has been since the first week of the 15.10 development cycle. I think that the Ubuntu Gnome developers would have something to say about claims that the Gnome desktop environment and Gnome shell being unstable in the 15.04 release.

I do not recommend installing an alternative desktop. You might want to try installing Ubuntu into a Linux Container (LXC). Then you can switch from Kubuntu on tty7 to Ubuntu on tty8. You also need something called lxc-desktop. Here are the links including one for a thread on this forum where I reported the results on my own experiments. Remember, my failures were more to do with wanting to get a development version runninig in a container. It works better when installing released versions.

[https://help.ubuntu.com/community/LXC](https://help.ubuntu.com/community/LXC)

[https://github.com/ustuehler/lxc-desktop](https://github.com/ustuehler/lxc-desktop)

[http://ubuntuforums.org/showthread.php?t=2271655](http://ubuntuforums.org/showthread.php?t=2271655)

My machine does not have the power for a VM but LXC did not have any additional resource overhead because we switch from one tty to another.

Regards.

---

### Post by alexel2 on 2015-10-17
Thank you very much! That really helps a lot. Deep apologies for the late reply too, I've had many frantic endeavours with independent studies as of late. Thank you again.

---

### Post by alexel2 on 2015-10-17
> **howefield said:**
> Yes, it's possible. Although you can install Unity as opposed to the full blown ubuntu-desktop packages.



A dual booting machine seems to be what you want with Kubuntu and Ubuntu each having separate partitions on your hard disk, the least complicated way for someone new ? Give the machine to someone else and get them to do it for you.

Before you start ensure that all important data is safely backed up so that your next thread will not be of the "how to recover data" kind. 

If it were mine, I'd image the drive with Clonezilla to give a way back to the starting point then partition the disk making space for Ubuntu and install into it. How large is your disk and what is currently on it ?


I apologize for the late reply. I am comfortable adding repos, installing packages, editing config files and such, but I was just curious as to whether or not it would be possible to utilize different versions of separate desktop environments without having to allocate partitioned space. I was informed the latest Unity environment is not unstable and it is in fact, KDE which is at fault (being bleeding edge and all). Again, deep apologies and thank you for taking the time to reply to this post, really.

---

### Post by alexel2 on 2015-10-17
> **grahammechanical said:**
> Each version of Ubuntu has its own repositories that are used by Ubuntu and the flavours. If you put the URL to the main trusty (15.04) repository into the list of software sources for a vivid (15.04) system you will most definitely get errors when you update. If we use 15.04 and install an alternative desktop we get the appropriate software from the 15.04 repositories.

I do not agree that that Ubuntu 15.04 is somewhat unstable. I am using Ubuntu 15.10 and that is fantastically stable and has been since the first week of the 15.10 development cycle. I think that the Ubuntu Gnome developers would have something to say about claims that the Gnome desktop environment and Gnome shell being unstable in the 15.04 release.

I do not recommend installing an alternative desktop. You might want to try installing Ubuntu into a Linux Container (LXC). Then you can switch from Kubuntu on tty7 to Ubuntu on tty8. You also need something called lxc-desktop. Here are the links including one for a thread on this forum where I reported the results on my own experiments. Remember, my failures were more to do with wanting to get a development version runninig in a container. It works better when installing released versions.

[https://help.ubuntu.com/community/LXC](https://help.ubuntu.com/community/LXC)

[https://github.com/ustuehler/lxc-desktop](https://github.com/ustuehler/lxc-desktop)

[http://ubuntuforums.org/showthread.php?t=2271655](http://ubuntuforums.org/showthread.php?t=2271655)

My machine does not have the power for a VM but LXC did not have any additional resource overhead because we switch from one tty to another.

Regards.


I didn't mean to say Ubuntu was directly at fault. I suppose it really has to do with KDE's newer and immature environment. I am new to Linux, but not the concepts it utilizes. That being said it would still be better  to be advised by more experienced users, and all replies in this thread have lead to many possible solutions. Thank you for taking your time to help me. I deeply apologize for my untimely response.

---

### Post by Bucky Ball on 2015-10-17
If you are using the currently supported Kubuntu/KDE, it is not bleeding edge. If you are using the nightly builds, it is.

---

