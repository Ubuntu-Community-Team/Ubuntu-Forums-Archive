---
title: "Firefox realplayer/WMP plugins not available"
date: 2006-03-01
forum: Desktop Environments
---

### Post by JohnnyWalker on 2006-03-01
I will post some problems a new user will encount when moving from windows to Ubuntu.

The first problem was that firefox is not upgradable using apt-get (which claims 1.07 is the latest).

The second problem I have had is that I have not found any convenient way to install realplayer plugin into firefox. (I have seen some info about installing and copying individual files into directories, which source and destination names I have to figure out myself :-|) Cant this be solved with an ubunto package?

The same goes for WMP, which is also not possible to click in the browser and a stream opens up.


I believe theese problem, missing media plugins are the first someone will encounter when starting to use ubunto.

---

### Post by stalefries on 2006-03-01
There is a guide to install Firefox 1.5 somewhere in these forums. I'm sure someone will provide the link before I finish typing this.

I don't know about realplayer.

I use mplayer, with the mozilla-player plugin and w32codecs to watch wmv's.

---

### Post by JohnnyWalker on 2006-03-01
Installing realplayer so that it works with mozilla in ubuntu is possible following the below, but This is NOT user friendly and IMO it has to solved within the application installer.

How do I install RealPlayer?

    RealPlayer can be installed using several different methods, although the recommended method is to install the Debian package. Download the RealPlayer 10 Debian package, and install it by running the following commands from a terminal:

    cd ~/Desktop
    sudo apt-get install libstdc++5
    sudo dpkg -i realplayer_10.0.6-0.0_i386.deb

---

### Post by Perfect Storm on 2006-03-01
You could try automatix, check my signature (which also install ff 1.5)

Another way is to open the terminal (applications ---> accessories  ---> terminal)

type:
```
sudo gedit /etc/apt/sources.list
```

add:
[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

then write in the terminal:
```
sudo apt-get update
sudo apt-get install realplay
```

---

### Post by JohnnyWalker on 2006-03-01
For WMP. I installed the w32codecs and mplayer. When I clicked a media file mplayer opened and complained about a missing font file. When installing the font file it stopped to complain, but I still cannot use the media file, nothing happens.

If someone wants to try, the mediafiles are the ones with a TV icon on page: [www.dr.dk/grandprix](www.dr.dk/grandprix)

---

### Post by Perfect Storm on 2006-03-01
Works here. You need mplayerplug-in.

Here's mplayerplug-in: [http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb)

Save it to your desktop

```
cd Desktop
sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
```

Though it's a bit "old" it should work. Another option would be compiling thte newest: [http://mplayerplug-in.sourceforge.net/download.php](http://mplayerplug-in.sourceforge.net/download.php) which works better. I'll help if needed.

---

### Post by JohnnyWalker on 2006-03-02
The link does not work, so I tried with apt-get, it seams it is installed.

vmware@vmware-bavm:~$ sudo apt-get install mplayerplug-in
Reading package lists... Done
Building dependency tree... Done
Package mplayerplug-in is a virtual package provided by:
  mozilla-mplayer 3.17-1ubuntu1~breezy1
You should explicitly select one to install.
E: Package mplayerplug-in has no installation candidate
vmware@vmware-bavm:~$ sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
mozilla-mplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Perfect Storm on 2006-03-02
The link works fine here.

---

