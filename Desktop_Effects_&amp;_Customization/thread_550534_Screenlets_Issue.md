---
title: "Screenlets Issue"
date: 2007-09-14
forum: Desktop Effects &amp; Customization
---

### Post by modestmelody on 2007-09-14
Whenever I try and update I get this error:


E: /var/cache/apt/archives/screenlets_0.0.10-3_i386.deb: trying to overwrite `/usr/share/applications/FlowerScreenlet.desktop', which is also in package screenlets-core


Screenlets can't update for weeks now, have lost the ability to keep settings after closed and don't start on startup.

Any ideas?

---

### Post by njknight on 2007-09-14
mmmmmm, not sure about you path to screenlets - that's more like where the deb file is.  You should have the screenlets located in /usr/local/share/screenlets/

I've added my screenlets (I use the weather, and the now Playing Screenlet) into my session manager  - just add an entry for each so that they start with the session.  just give the entry a name and in the comand, paste the full path to the screenlet that you want to use eg the path for my weather screenlet is /usr/local/share/screenlets/Weather/WeatherScreenlet.py > /dev/null & 

The /dev/null bit just tells it really not to display any errors.

---

### Post by FuturePilot on 2007-09-14
Try
```
sudo apt-get remove --purge screenlets-core
```

---

### Post by smartboyathome on 2007-09-14
> **FuturePilot said:**
> Try
```
sudo apt-get remove --purge screenlets-core
```

Or just choose completely remove in Synaptic Package Manager. ;)

---

### Post by modestmelody on 2007-09-14
```
jason@jason-desktop:~$ sudo apt-get remove --purge screenlets-core
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtk-canvas1 libart2 gdk-imlib1 libgtkmm1.2-0c2a libberylsettings0
  python-feedparser imlib-base gdk-imlib11 libsigc++0c2 beryl-plugins-data
  libberyldecoration0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  screenlets
The following packages will be REMOVED:
  screenlets-core* screenlets-utils*
The following packages will be upgraded:
  screenlets
1 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/344kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 140661 files and directories currently installed.)
Preparing to replace screenlets 0.0.9-1 (using .../screenlets_0.0.10-3_i386.deb) ...
Unpacking replacement screenlets ...
dpkg: error processing /var/cache/apt/archives/screenlets_0.0.10-3_i386.deb (--unpack):
 trying to overwrite `/usr/share/applications/FlowerScreenlet.desktop', which is also in package screenlets-core
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/screenlets_0.0.10-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by modestmelody on 2007-09-14
Ah, using synaptic worked.  Thanks guys.

---

