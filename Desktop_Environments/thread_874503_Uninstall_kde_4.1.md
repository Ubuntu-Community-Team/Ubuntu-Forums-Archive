---
title: "Uninstall kde 4.1?"
date: 2008-07-30
forum: Desktop Environments
---

### Post by CC_Joe on 2008-07-30
So, I'm new to ubuntu (been using 8.04 for just a few months), and I saw that KDE 4.1 was out so I decided to see what it was all about.

I installed it by using ```
apt-get update && sudo apt-get install kubuntu-kde4-desktop
```

Installation worked perfectly. I checked out KDE, it seemed cool. However, I've noticed that FireFox 3 doesn't play embedded videos any more =/

If anyone knows why this happened, great. However, I am quite happy with Gnome so I'm just leaning towards uninstalling KDE to see if that fixes my problems. I tried using ```
sudo apt-get remove kubuntu-kde4-desktop
``` however, that just uninstalled a really small file and left everything else.

Anyone know the correct command?

---

### Post by newman on 2008-07-30
sudo apt-get purge remove kubuntu-kde4-desktop

---

### Post by CC_Joe on 2008-07-30
darn =/

```
joe@Snow-Crash:~$ sudo apt-get --purge remove kubuntu-kde4-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kubuntu-kde4-desktop is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-backports-modules-2.6.24-18-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
```

didn't work.

Since I was missing one small file from the first time I tried to uninstall, I reinstalled kde4 which gave me back that file. But then I tried your command again and got this:

> joe@Snow-Crash:~$ sudo apt-get --purge remove kubuntu-kde4-desktopReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-backports-modules-2.6.24-18-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kubuntu-kde4-desktop*
0 upgraded, 0 newly installed, 1 to remove and 36 not upgraded.
After this operation, 32.8kB disk space will be freed.
Do you want to continue [Y/n]? 

Soo... doesn't look like that command is acting how I want it to act.

My third attempt was 

> joe@Snow-Crash:~$ sudo aptitude purge kubuntu-kde4-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  linux-backports-modules-2.6.24-18-generic 
The following packages have been automatically kept back:
  avant-window-navigator-data-trunk avant-window-navigator-trunk 
  kdebase-data-kde4 kdebase-plasma-kde4 libavcodec1d libavformat1d 
  libavutil1d libawn0-trunk libkonq5 libkonq5-templates libpostproc1d 
  libqt4-core libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 
  python-awn-trunk 
The following packages have been kept back:
  awn-extras-applets-trunk awn-manager-trunk dolphin-kde4 
  evolution-exchange firefox firefox-3.0 firefox-3.0-gnome-support 
  firefox-gnome-support kate-kde4 kdebase-bin-kde4 konqueror-kde4 
  konqueror-nsplugins-kde4 konsole-kde4 libpoppler-glib2 libpoppler2 
  poppler-utils strigi-daemon ufw xulrunner-1.9 xulrunner-1.9-gnome-support 
The following packages will be REMOVED:
  kubuntu-kde4-desktop{p} 
0 packages upgraded, 0 newly installed, 2 to remove and 36 not upgraded.
Need to get 0B of archives. After unpacking 1327kB will be freed.
Do you want to continue? [Y/n/?] n
Abort.

That's more promising, but kde was about 400 megs. What am I missing?

---

### Post by CC_Joe on 2008-07-30
So it turns out, upon restart, firefox plays videos again. I'm not sure if my uninstall fiasco solved my problem or not, but at least it's solved!

However, I think I'd still like to know how to uninstall KDE, for knowledge's sake.

---

### Post by sandeepy on 2008-07-30
sudo aptitude remove kde4-desktop

this should remove the dependencies too.

About why firefox does not play videos, that's because you might not be linking your mplayer with firefox. I think that Gnome will use its own firefox version (correct me if I am wrong).

---

### Post by CC_Joe on 2008-07-30
> joe@Snow-Crash:~$ sudo aptitude remove kde4-desktop
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find package "kde4-desktop".  However, the following
packages contain "kde4-desktop" in their name:
  kubuntu-kde4-desktop 
Couldn't find package "kde4-desktop".  However, the following
packages contain "kde4-desktop" in their name:
  kubuntu-kde4-desktop 
The following packages are unused and will be REMOVED:
  blt dvdauthor libtwolame0 linux-backports-modules-2.6.24-18-generic 
  mencoder normalize-audio python-dev python-tk python2.5-dev tcl8.4 tk8.4 
  txt2tags 
The following packages have been automatically kept back:
  avant-window-navigator-data-trunk avant-window-navigator-trunk 
  kdebase-data-kde4 kdebase-plasma-kde4 libavcodec1d libavformat1d 
  libavutil1d libawn0-trunk libkonq5 libkonq5-templates libpostproc1d 
  libqt4-core libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 
  python-awn-trunk 
The following packages have been kept back:
  awn-extras-applets-trunk awn-manager-trunk dolphin-kde4 
  evolution-exchange firefox firefox-3.0 firefox-3.0-gnome-support 
  firefox-gnome-support kate-kde4 kdebase-bin-kde4 konqueror-kde4 
  konqueror-nsplugins-kde4 konsole-kde4 libpoppler-glib2 libpoppler2 
  poppler-utils strigi-daemon ufw xulrunner-1.9 xulrunner-1.9-gnome-support 
0 packages upgraded, 0 newly installed, 12 to remove and 36 not upgraded.
Need to get 0B of archives. After unpacking 26.6MB will be freed.
Do you want to continue? [Y/n/?] 



So, this removes 26 mb. I'm looking to remove all of the programs that came with kde as well. Any way I can do that in one fell swoop?

---

### Post by Thermo1 on 2008-07-30
I found this over in [this thread]("http://ubuntuforums.org/showthread.php?t=874818"):

```
sudo aptitude purge kubuntu-kde4-desktop
sudo aptitude purge kdm-kde4
sudo dpkg-reconfigure kdm
sudo aptitude purge ~nkde4
```

---

### Post by imronak on 2008-07-31
```
sudo dpkg-reconfigure kdm
```

This is a VERY IMPORTANT STEP, because if you miss that, you wont get your default (may be gnome) back and you will be logged on to a command line. I was in the same situation :-/

Then, I found out that /etc/X11/defualt-display-manager has not been updated since the uninstall, if this a bug/a missed check at uninstall?

---

### Post by patrickaupperle on 2008-08-11
I know this thread is kind of old, but I found something that helps. Remove the kde 4.1 repo line, then in synaptic remove most of the stuff under local or obsolete. Be careful and watch the dependencies.

---

### Post by woaibbhemm on 2008-08-12
hello~
    nice   to  meet  you   and     thank  you   for   youe   sharing ,  welcome   to   our   website  !












Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by Jackelope on 2008-09-16
The post below solved it for me =). Looks like its completely gone.

[http://ubuntuforums.org/showthread.php?t=677588T](http://ubuntuforums.org/showthread.php?t=677588T)

---

