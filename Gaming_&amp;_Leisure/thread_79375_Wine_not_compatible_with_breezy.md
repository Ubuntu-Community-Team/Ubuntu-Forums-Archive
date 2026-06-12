---
title: "Wine not compatible with breezy?"
date: 2005-10-20
forum: Gaming &amp; Leisure
---

### Post by ramba on 2005-10-20
It seems that it's impossible to install wine in breezy (amd64), I'm I right on this? If someone has managed to install it, tell me exactly what you did to make it work! Does someone know if ubuntu will provide its own package?

(Uhm... thanks?) :confused:

---

### Post by Havoc on 2005-10-20
It is generally known that wine has some problems running on a 64 bit platform.

Are you running Breezy on a 64 bit Breezy (Meaning kernel) or are you using the normal i386 Breezy?

---

### Post by ramba on 2005-10-20
Well, I downloaded the amd64.iso and installed it. That's all I know.

---

### Post by pinoyskull on 2005-10-20
wine on breezy i386 has no problems at all, haven't tried it on a 64 machine yet

---

### Post by S29K on 2005-10-20
'No problems at all' is somewhat misleading as I have had enough problems with to send me back to Hoary.  The lack of a version of WineTools that works with the current Wine release makes installation and configuration tricky at best.  

The app I need to run will not run in Wine/Breezy but works fine in Wine/Hoary.  I'm not sure of what is causing the problem exactly but don't have weeks to figure it out either.

When deciding which version of packages to include in the Breezy repositories, despite people complaining that the listed version is not the most current version, waiting until a complete solution is available would be preferable to including one that doesn't work as well as the older one.

---

### Post by pinoyskull on 2005-10-21
sidenet's tool is compatible with the newer version of wine

---

### Post by Perfect Storm on 2005-10-21
[QUOTE=S29K]'No problems at all' is somewhat misleading as I have had enough problems with to send me back to Hoary.  The lack of a version of WineTools that works with the current Wine release makes installation and configuration tricky at best.  

The app I need to run will not run in Wine/Breezy but works fine in Wine/Hoary.  I'm not sure of what is causing the problem exactly but don't have weeks to figure it out either.

When deciding which version of packages to include in the Breezy repositories, despite people complaining that the listed version is not the most current version, waiting until a complete solution is available would be preferable to including one that doesn't work as well as the older one.[/QUOTE]

Have you Tried adding wine repo to your source list and see if they are better?

```

sudo gedit /etc/apt/sources.list

```

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

```
sudo apt-get update
sudo gedit /etc/apt/preferences
```

Package: wine
Pin: release l=WineHQ APT Repository
Pin-Priority: 1000

---

### Post by S29K on 2005-10-21
I tried sidenet which was able to install IE6 and some other MS stuff but my required app still would not run.  I tried the sourceforge repos as well but they made no difference.  My suspicion is that there is something different about Gnome 2.12 that is causing the problem as the errors that I am getting are graphical in nature.  The app is essential a text emulator that draws an entire screen of text in a menu-like terminal environment.  What actually comes up is a graphical representation of the text, twisted and angled downwards....mostly unreadable and certainly not right.

I am going to experiment with KDE to see if it makes any difference.

---

### Post by S29K on 2005-10-21
I tried the changes suggested by Artificial Intelligence in Hoary and the new version of Wine that I 'upgraded' to caused the app to exhibit the same behaviour as in Breezy.  Obviously the problem is with the newest Wine version and perhaps not with Breezy, or Gnome.

Is there a way to specify in the apt-preferences the version of the package as well as the preferred repo?

---

### Post by Perfect Storm on 2005-10-21
I concurre (sp?) what S29K says. It seems there some problem with wine. My nwn install which requires wine to install nwn as native couldn't find or use the new version of wine, instead I had to rely on the old binary wine which comes with the nwn installer.

---

### Post by Corvash on 2005-11-10
Attempting to install source packages on AMD 64 as per: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

```
root@aegis:/etc/apt# apt-get build-dep wine
Reading package lists... Done
Building dependency tree... Done
Package mesa-common-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  mesa-doc libgl1-mesa-dev
E: Build-dependencies for wine could not be satisfied.
```

Fix? Workaround?

---

### Post by AndersAA on 2005-11-10
I believe ubuntu doesn't have both amd64 and i386 kernel headers, which makes building wine on ubuntu very tricky.

---

### Post by TICK66 on 2005-11-29
Below is what i get when trying to install wine .


tick66@leviathon:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
tick66@leviathon:~$

---

### Post by AndersAA on 2005-11-29
as I said, you can't build wine on amd64, you can however grab the wine slackware binary package from winehq.com and find the two libs you need (along with ia32 libs from synaptics).

missing libs : libXxf86dga.so.1  libXxf86vm.so.1

---

### Post by aldmal on 2005-11-30
I have the same question. I'm running i386 version of Breezy.

I used Automatrix to get Wine and install it. I then went to my NTFS drive and opened a Windows app and it worked fine. I opened by right clicking and then selecting "Open with Wine" That was the last time Wine worked!

When I type   "winecfg" I get the following text:
  X  Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  13
  Current serial number in output stream:  14

Not to be scared off by some giberish, I turned to the Wine Manaul and read it. Nothing worked. Every time I enter a Wine command I get the same message. The only one that works is "Wine --versions" which returns a 0.9.2 which is the current version.

Via "apt-get --purge remove" I removed Wine. This was recommended in the Wine troubleshotting section. I then ran update and install to be sure I had the most recent version and a clean install. Everything went fine. 

So back to winecfg and back to the same message.

Any and all suggestions are appreciated.

---

### Post by Perfect Storm on 2005-11-30
add this to the repo:

```

sudo gedit sudo gedit /etc/apt/sources.list

```

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/


```

sudo gedit /etc/apt/preferences

```

Package: wine
Pin: release l=WineHQ APT Repository
Pin-Priority: 1000

```

sudo apt-get update
sudo apt-get install wine winetools
winetools

```

---

