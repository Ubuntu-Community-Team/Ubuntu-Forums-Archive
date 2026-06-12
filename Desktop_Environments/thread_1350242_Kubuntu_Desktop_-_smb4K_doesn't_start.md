---
title: "Kubuntu Desktop - smb4K doesn't start"
date: 2009-12-09
forum: Desktop Environments
---

### Post by piedro on 2009-12-09
Hi! 

I installed smb4K - which i used since intrepid for mounting samba shares on a NAS. Since I can't find any other solution to have my network folders out of dolphin to show up in common applications like quanta+, vlc, virtualbox e.g., I installed version 0.10.2 of smb4K in karmic. When started it states something like: 

> Either your PATH-settings are incorrect or you're missing the following packages: nmblookup, net 

please fix and try again!


What can I do now? 

Samba 2.3.4 is installed, a package nmblookup doesn't exist in the software repositories neither does "net". 

How could my PATH-Environment not be allright, what is meant exactly and how to fix this? 

Is there another solution to access network folders (with the non KDE 4.3 applications) with CIFS without making permanent entries within the fstab. (Computers get connected and disconnected to the network, so a permanent soltuion doesn't seem to be right!) 

thx, piedro

---

### Post by Zorael on 2009-12-09
**net** and **nmblookup** in **/usr/bin/** are supposed to be symlinks to **net** and **nmblookup** in **/etc/alternatives/** - which are symlinks in turn. Where *these* symlinks point can then be managed by using **update-alternatives**. The real executables are located in **/usr/bin/**, as **net.samba3** and **nmblookup.samba3** respectively. This setup is likely caused by samba 4 being in development; to allow people to easily switch between net.samba3 and net.samba4, etc.

So one approach would be to try reinstalling **samba-common-bin** and see if it straightens out the symlinks.
```
$ sudo aptitude reinstall samba-common-bin
```
If that doesn't fix it right away, see if the symlinks exist at all.
```
$ file /usr/bin/net /usr/bin/nmblookup
[B][COLOR="Green"]/usr/bin/net:       symbolic link to `/etc/alternatives/net'
/usr/bin/nmblookup: symbolic link to `/etc/alternatives/nmblookup'[/COLOR][/B]
```
If they don't, link them to their **/etc/alternatives/** symlinks.
```
$ sudo ln -s /etc/alternatives/net /usr/bin/net
$ sudo ln -s /etc/alternatives/nmblookup /usr/bin/nmblookup
```

To manage the net/nmblookup alternatives (via update-alternatives), do this.
```
$ sudo update-alternatives --config net
$ sudo update-alternatives --config nmblookup
```
Just tell it to point to the ***.samba3** alternatives, if asked.

---

### Post by piedro on 2009-12-09
thx Zorael! 

This worked. First I just reinstalled with Synaptic because I find these warnings everywhere not to mix the use of apitude with synaptics. I used synaptics all the way and now ... 

I took your advice and that's it. I'm a bit worried though. Does it harm my system to use synaptics after using aptitude? Cause I like to stick to system integrated apps as far as possible.  

Anyway the original problem is solved. 

thx, 
piedro

---

### Post by Zorael on 2009-12-09
Mixing use of Synaptics and aptitude shouldn't reallly have any harmful side-effects, no. While they don't always listen to eachothers' settings, they both work via dpkg (the Debian package management system), so in a sense they're simply different frontends to the same thing.

An example of when they don't listen to eachother would be if you tell aptitude to hold a package; to stop it from being upgraded. If so told, aptitude would dutifully hold it - but you would have to independently tell Synaptic to also hold it.

---

### Post by piedro on 2009-12-09
thx for the explanation! 

have a nice day, 
piedro

---

