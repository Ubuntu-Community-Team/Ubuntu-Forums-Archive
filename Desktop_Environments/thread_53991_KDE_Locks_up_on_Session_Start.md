---
title: "KDE Locks up on Session Start"
date: 2005-08-03
forum: Desktop Environments
---

### Post by Safyre on 2005-08-03
Hi everyone, I've been thrilled with Kubuntu and have everything set up just as I like it. Suddenly, my poor system can't finish booting up KDE, it gets to 87% and stops. The mouse continues to function, but KDE just stops. I can run programs in failsafe, and the computer responds just fine there. Something similar happened to my SuSE install, which is what prompted me to switch to Ubuntu. 
Any ideas? I'm at a loss. I've tried killing Skype, which was running in a previous session, by relocating the executable to the desktop so KDE can't restart it. If I remember correctly, that worked once before, but then the next startup returned to this sad state. I've left this computer and its disease to sit for a few weeks, but the time has come to face the midi. 
Thanks for any help you can provide, I love this distro and want to keep using it. 
~Safyre

---

### Post by cwaldbieser on 2005-08-03
Could you try running kde from the console (for example in an Ubuntu Nestx window or from one of the virtual consoles) so you could see the diagnostic messages?  Do you have any idea what stage of the initialization it freezes on?

---

### Post by ltmon on 2005-08-03
Try deleting the following directories:

> rm -rf ~/.kde/socket-<hostname>
> rm -rf ~/.kde/tmp-<hostname>
> rm -rf ~/.kde/cache-<hostname>

This deletes all cached and temporary information for kde, and you may have better luck when restarting.

If not, check the permissions and ownership of ~/.ICEauthority.  You should own and have read/write access to this file.  This file having bad permissions is a common cause of kde login issues.

Hope one of these works.  They're (in my experience) the two most common causes of KDE problems.

L.

---

### Post by Safyre on 2005-08-03
I tried cleaning out those folders as was suggested, to no avail. KDE behaves just as before.
I've been trying to figure out how to start KDE through the failsafe console- but I haven't been successful there either. How do I start up a Nestx window or other such console? Thanks so much!
It's the kind, knowledgeable people such as yourselves who make Linux possible for those of us who don't know what we're doing but want to play too.

---

### Post by cwaldbieser on 2005-08-03
Well, do you have the Gnome (Ubuntu) or xfce desktops installed that you can log in with?  If so, you can install NestX from synaptic.  You run it by doing something like:
```

$ Nestx :1
```

Then you can open another console and run:
```
$ xterm -display :1
```
This should make an xterminal open up in the nested X display.  In that terminal, you should be able to run:
```
$ startkde
```
Any errors and diagnostics should be sent to that console.  If you want to send them to files, try:
```
$ startkde > kde_log.txt 2> kde_errors.txt
```

If you don't have another desktop installed, you could try downloading one with apt-get.

---

### Post by Safyre on 2005-08-04
Well by attempting to install Gnome (which has yet to run, but that's beside the point) some of the packages allowed kde to show error messages it hadn't been able to before. I fixed those errors (no write access to a folder, etc.) and then tried to run KDE in failsafe terminal again. It showed me that Kaffeine was trying to start up and unsucessfully begin a playlist, when kaffeine was already open in that session, apparently. I moved Kaffeine so that error couldn't happen, and now KDE starts just fine. Thanks so much. If you hadn't showed me that simple command, kdestart, this computer would have been fried.

---

