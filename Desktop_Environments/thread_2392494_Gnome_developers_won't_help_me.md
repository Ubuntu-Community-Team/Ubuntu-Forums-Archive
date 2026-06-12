---
title: "Gnome developers won't help me"
date: 2018-05-21
forum: Desktop Environments
---

### Post by Keith Myers on 2018-05-21
I have posted in the gnome developers forum and am on the buglist for "application won't dock".  My application developers say the problem lies with Gnome since it works in all previous distribution and Unity.  My applications code has not changed.  The gnome developer says the issue lies with my application.  So each party is putting the fault with the other.  This does not help me in any way.

---

### Post by kerry_s on 2018-05-21
so what are you asking for us to do?

i can only assume your talking about a *.desktop file that has no right click-> add to favorites ?

can you post the *.desktop ?

---

### Post by Keith Myers on 2018-05-21
I was successful a couple of times in my many file iterations to write a boincmgr.desktop file that gave me the "Add to favorites" menu which allowed me to dock the application.  However all the application does when launched from the dock is open the Boinc Manager window.  It does not launch the required boinc client part of the application which means the background main engine is not running and therefore the app does nothing.

Launching the boinmgr application directly from the BOINC folder opens the Manager window and connects with the client normally.  The boincmgr docks normally and launches both the manager and client in 17.10 and lower distributions.

Nothing in the BOINC code has changed from 17.10 release.  So the developer states the problem lies with 18.04 and Gnome.  The Gnome developer says the BOINC developer has to fix BOINC to run on 18.04 Gnome.  Neither party says there is anything wrong.  This is the last iteration I have tried and is the 17.10 Unity boincmgr.desktop file and I have simply changed Unity to Gnome in the callout.  I removed those lines in another iteration and it made no difference.

```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Name=BOINC Manager
Icon=boincmgr.png
Path=/home/keith/BOINC
Exec=/home/keith/BOINC/boincmgr
StartupNotify=false
StartupWMClass=Boincmgr
OnlyShowIn=Gnome;
X-GnomeGenerated=true

```

---

### Post by kerry_s on 2018-05-21
try putting the command into a script & launching that.

example boincmgr.sh :
```
#!/bin/bash
/home/keith/BOINC/boincmgr
```

make it executable:
```
chmod +x boincmgr.sh
```

change your execute line:
```
Exec=/path/to/boincmgr.sh
```

i've had to do that to some of mine, i think it's a security thing, never bothered to look into it.

---

### Post by mc4man on 2018-05-21
Shouldn't the Path= be to boinc-client

---

### Post by Keith Myers on 2018-05-22
Not sure why that would be necessary.  boincmgr runs fine exactly as it is supposed to by just double-clicking it in its folder.  The issue is that it won't dock properly or execute from the dock.

---

### Post by Keith Myers on 2018-05-22
I don't use the repository version of BOINC.  I use the version written by the Linux/Mac developer and he posts his special versions at Crunchers Anonymous.  It is installed in a folder on the Desktop where you have the permissions already.  I hate the repository versions which bury the program in two directories with group permission you don't have access to without jumping through hoops.  The 7.4.44 and 7.8.3 versions are specially made to use the special CUDA 9 gpu application which has 2X-10X-fold performance over the stock Seti applications.

---

### Post by Keith Myers on 2018-05-22
So I can now dock Boinc Manager and it opens its window and starts the client.  I didn't do anything to the boincmgr.desktop file since my last post.  It started working apparently after I loaded a bunch of new packages to get a python program I use ready for use with its prerequisites.  Thank goodness for the History function in Synaptic.  Maybe someone can look at the packages I installed and state which was most likely to get the desktop file working.  This is what I installed.

libblas3 (3.7.1-4ubuntu1)
libgfortran4 (7.3.0-16ubuntu3)
liblapack3 (3.7.1-4ubuntu1)
python-numpy (1:1.13.3-2ubuntu1)
libmng2 (2.0.2-0ubuntu3)
libmysqlclient20 (5.7.22-0ubuntu18.04.1)
libqt4-dbus (4:4.8.7+dfsg-7ubuntu1)
libqt4-declarative (4:4.8.7+dfsg-7ubuntu1)
libqt4-designer (4:4.8.7+dfsg-7ubuntu1)
libqt4-help (4:4.8.7+dfsg-7ubuntu1)
libqt4-network (4:4.8.7+dfsg-7ubuntu1)
libqt4-script (4:4.8.7+dfsg-7ubuntu1)
libqt4-scripttools (4:4.8.7+dfsg-7ubuntu1)
libqt4-sql (4:4.8.7+dfsg-7ubuntu1)
libqt4-sql-mysql (4:4.8.7+dfsg-7ubuntu1)
libqt4-svg (4:4.8.7+dfsg-7ubuntu1)
libqt4-test (4:4.8.7+dfsg-7ubuntu1)
libqt4-xml (4:4.8.7+dfsg-7ubuntu1)
libqt4-xmlpatterns (4:4.8.7+dfsg-7ubuntu1)
libqtassistantclient4 (4.6.3-7build1)
libqtcore4 (4:4.8.7+dfsg-7ubuntu1)
libqtdbus4 (4:4.8.7+dfsg-7ubuntu1)
libqtgui4 (4:4.8.7+dfsg-7ubuntu1)
mysql-common (5.8+1.0.4)
python-qt4 (4.12.1+dfsg-2)
python-sip (4.19.7+dfsg-1)
qdbus (4:4.8.7+dfsg-7ubuntu1)
qt-at-spi (0.4.0-8)
qtchooser (64-ga1b6736-5)
qtcore4-l10n (4:4.8.7+dfsg-7ubuntu1)
libxdo3 (1:3.20160805.1-3)
xdotool (1:3.20160805.1-3)

The app that needed these packages is a Seti user developed app and the app is called Seti Rescheduler. It is a python application. This app also docks with the Ubuntu 16.04 Unity .desktop file borrowed from another machine.  But unlike with the unexpected change that enabled Boinc Manager to start working suddenly, this app doesn't work from the Dock. Works fine when launched from its folder.  Also borrowed from another machine where it works fine from the Launcher. This is its .desktop file.  Maybe someone can point out what is wrong with it.
```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Name=SETI Dynamic Task Rescheduler (v0.3)
Icon=/home/keith/Downloads/Rescheduler/Yin_yang.png
Path=/home/keith/Downloads/Rescheduler
Exec=python /home/keith/Downloads/setidtrsched.pyw
StartupNotify=false
StartupWMClass=setidtrsched.pyw
OnlyShowIn=Unity;
X-UnityGenerated=true

```

---

### Post by Keith Myers on 2018-05-28
Well I am going to close this thread and post as Solved by who knows how.  The next 18.04 computer conversion with the 16.04 .desktop file and the loadout of apps and packages I settled on for the first conversion computer has the BOINC application docking and launching normally

---

