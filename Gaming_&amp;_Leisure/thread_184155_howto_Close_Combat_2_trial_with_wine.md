---
title: "howto: Close Combat 2 trial with wine"
date: 2006-05-29
forum: Gaming &amp; Leisure
---

### Post by dolny on 2006-05-29
The aim of this small guide is to show you how to run Close Combat 2 Trial version on Ubuntu, using Wine.
CC2 info: [http://uk.gamespot.com/pc/strategy/closecombat2abridgetoofar/index.html](http://uk.gamespot.com/pc/strategy/closecombat2abridgetoofar/index.html)

1. Download wine:
- Add the wine repos to your /etc/apt/sources.list
- in console: ```
sudo apt-get install wine
```
2. Download the CC2: A Bridge Too Far Trial version:
- in console: ```
wget http://www.avault.com/pcrl/dlftp.asp?url=ftp.microsoft.com/deskapps/games/public/closecombat/MSABTF.EXE
```
3. Go to the dir you downloaded the CC2 file and:
- in console ```
wine MSABTF.EXE
```
- after the installation, go to the dir where you installed the demo (/home/your_username/.wine/...)
- in console ```
wine cc2trial.exe
```

In case the sound doesn't work:
1. Press F8 in the main menu and enable sound if it is possible.

If not:

2. Download wine tools and configure it (it was covered in other FAQs and you can read the info on the website, very easy)
- from [http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)
2. Choose cc2trial from the applications list, switch the Windows version to XP (I did so, probably not necessary), then move to the Audio tab and try different sound systems, Arts worked for me on KDE, and OSS on XFCE (weird?).

Enjoy.
If anybody had any luck running any full Close Combat version, please post the info here. I tried the CC2 from [http://www.the-underdogs.info](http://www.the-underdogs.info) but I couldn't unack the 'data.uha' file with wine. I bought CC: Invasion Normandy but I can't test it - it's at my home, and I'm in a different country now. Transgaming Database says it doesn't work. CC4 is said to be working with Wine (info from Wine App Database).

I hope somebody will find this small howto useful.

---

### Post by dolny on 2006-06-02
CC3 trial works under cedega.

---

