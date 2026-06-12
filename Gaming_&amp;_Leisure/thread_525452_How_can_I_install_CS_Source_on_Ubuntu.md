---
title: "How can I install CS Source on Ubuntu?"
date: 2007-08-14
forum: Gaming &amp; Leisure
---

### Post by vicisgoodtogo on 2007-08-14
Hello!
I'm a big nb and I have no idea of how to do it.
I installed Wine from add/remove.
What do I do now? :D

---

### Post by Swarms on 2007-08-14
First, install the newest Wine version.
Type this into your terminal of choice:
> wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
Then you will always have the newest public version.

Then you follow the guide from this nice website where you can find a lot of howto's.

[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

And when steam is installed you can install CSS through that.

---

### Post by vicisgoodtogo on 2007-08-14
Hey dude...
The second line said not found, but I think it's all good.
Anyways...
The link... Is like... Good... But... It's for experts or so...
It's kinda complicated.

---

### Post by dfreer on 2007-08-14
Basically, the main thing is to get steam installed correctly. Run *winecfg* in terminal once, so that it will create a virtual windows directory at *~/.wine/*
Then, find a copy of *tahoma.ttf*, either on your windows PC at *C:\WINDOWS\FONTS\*, or somewhere online. Copy this to your *~/.wine/drive_c/windows/fonts/* folder.
Then run this command in terminal to download the gecko engine, it basically handles web browsing and viewing the steam store:
```
wine iexplore www.google.com
```
After that, download the steam installer to your desktop (you can use your normal web browser for this, no need for *iexplore*) and install it like so:
Using the old SteamInstaller.exe
```
wine ~/Desktop/SteamInstaller.exe
```
Using the new SteamInstaller.msi
```
wine msiexec /i ~/Desktop/SteamInstaller.msi
```
From there, using steam you can install your steam games.

There are plenty of threads concerning CS Source and steam installation on the forums here, btw ;)

---

### Post by ubuntuforums on 2007-08-14
hmm...  Get Cedega.  ;)

---

### Post by Swarms on 2007-08-14
> **ubuntuforums said:**
> hmm...  Get Cedega.  ;)

No way when CSS runs flawlessly, waste of money.

---

### Post by mightyzug on 2007-09-25
screw cedega.

they aren't doing anything at all in terms of helping you run cs, they merely provide a frontend

that certainly does not deserve any of my money

---

### Post by Vadi on 2007-10-12
Hmm, I get this:

vadi@vadi-laptop:~/Downloads$ wine msiexec /i ~/Desktop/SteamInstaller.msi
err:msi:copy_package_to_temp failed to copy package L"/home/vadi/Desktop/SteamInstaller.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002!
vadi@vadi-laptop:~/Downloads$ 


What am I doing wrong?

---

### Post by dfreer on 2007-10-12
Try downloading the old SteamInstall.exe instead, it still works. Other than that, did you type the filename in correctly?

---

### Post by Vadi on 2007-10-12
Okay, found a .exe, I'll try it. Yes, I did verify the file name was correct.

---

### Post by Vadi on 2007-10-12
Ahh, meh. Some steam error, "unable to start steam engine:the registry is un use by another process". But I guess that's more googling.

By the way, I got the .exe from here ([click]("http://halflife2.filefront.com/files/Half-Life/Official_Releases/Steam;2934")).

---

### Post by dfreer on 2007-10-12
I find it useful, when installing steam, to wipe my ~/.wine/ directory and start fresh. Obviously, if you have already installed XYZ program, you're going to need to back it up, or figure out some other solution. Just make sure to follow the steps again (run iexplore, winecfg, and copy the tahoma.ttf file).

If you don't want to wipe ~/.wine/, or have tried the installation already once, you can always check and make sure that no wine processes are still running in your system monitor (including steam.exe!), and also check your wine virtual system monitor with this:
```
wine taskmgr
```

---

### Post by Vadi on 2007-10-12
Yes, I started it again, and it worked. Thanks!

---

