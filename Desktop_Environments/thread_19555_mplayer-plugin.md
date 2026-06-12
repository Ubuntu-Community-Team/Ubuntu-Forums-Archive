---
title: "mplayer-plugin"
date: 2005-03-12
forum: Desktop Environments
---

### Post by nix4me on 2005-03-12
How do I get mplayer-plugin installed into firefox?  I dont see it in synaptic anywhere.
 
Thanks,
mark

---

### Post by bored2k on 2005-03-12
[QUOTE=nix4me]How do I get mplayer-plugin installed into firefox?  I dont see it in synaptic anywhere.
 
Thanks,
mark[/QUOTE]
 Get the following line inside your "/etc/apt/sources.list" file
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

Then sudo apt-get install mozilla-mplayer.

---

### Post by lorap on 2005-03-12
hi buddy!
you can install vlc player so y'd be able watch movies & listen to the music.
go to synaptic then choose the option settings,then to repositories,then mark there all options,press ok,after what press reload button,then press search button and write vlc then press ok.after that install it.works great,no codec needed.
have a nice day friend!
pavel

---

### Post by nix4me on 2005-03-12
[QUOTE=bored2k]Get the following line inside your "/etc/apt/sources.list" file
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

Then sudo apt-get install mozilla-mplayer.[/QUOTE]


This repository did not work.  Package not found. 
Mark

---

### Post by bored2k on 2005-03-12
[QUOTE=nix4me]This repository did not work.  Package not found. 
Mark[/QUOTE]
 bored@noir:~$ apt-cache search mozilla-mplayer
mozilla-mplayer - MPlayer-Plugin for Mozilla, Konqueror and OpenOffice.org

I highly doubt the repository did not work. Most of us use it, I just did a fresh Hoary install and I am using it.

---

### Post by flyfishin on 2005-03-12
[https://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-20.3414506543/](https://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-20.3414506543/)

In the page the instructions list warty, change that to hoary and enable universe in /etc/apt/sources.list.  Then do an **aptitude update** and **aptitude install mplayerplug-in**

---

### Post by nix4me on 2005-03-12
[QUOTE=bored2k]bored@noir:~$ apt-cache search mozilla-mplayer
mozilla-mplayer - MPlayer-Plugin for Mozilla, Konqueror and OpenOffice.org

I highly doubt the repository did not work. Most of us use it, I just did a fresh Hoary install and I am using it.[/QUOTE]

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main



root@ubuntu:/home/nix4me/proftpd-1.2.10 # apt-get install mozilla-mplayer
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package mozilla-mplayer

Mark

---

### Post by bored2k on 2005-03-12
[QUOTE=nix4me]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main



root@ubuntu:/home/nix4me/proftpd-1.2.10 # apt-get install mozilla-mplayer
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package mozilla-mplayer

Mark[/QUOTE]
 bored@noir:~$ cat /etc/apt/sources.list; apt-cache search mozilla-mplayer
#deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
mozilla-mplayer - MPlayer-Plugin for Mozilla, Konqueror and OpenOffice.org

---

### Post by flyfishin on 2005-03-12
[QUOTE=nix4me]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main



root@ubuntu:/home/nix4me/proftpd-1.2.10 # apt-get install mozilla-mplayer
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package mozilla-mplayer

Mark[/QUOTE]


You don't have multiverse enabled.  That is where mplayerplug-in is located.

---

