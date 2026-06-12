---
title: "Keepasx not working Ubuntu 11.10 Unity"
date: 2011-10-14
forum: Desktop Environments
---

### Post by lucacerone on 2011-10-14
Hi,
after the upgrade to Ubuntu 11.10 Keepasx doesn't work properly when using Unity.
When I launch it I'm able to enter the master password of the databases,
but then the main window is not shown.

If I login using Gnome (no effects) then Keepasx works correctly (so maybe is an issue with Compiz?)
Any idea how to find and solve the problem?

Thanks a lot,
Luca

---

### Post by barjea on 2011-10-15
I have exactly the same issue.

---

### Post by gamblor01 on 2011-10-15
It's working great for me after the upgrade, I just used it this morning and had it perform global auto-type and everything.  Have you tried uninstalling it and then reinstalling it?  You might also want to look at the libqt libraries on your system, and possibly reinstall those as well since keepassx relies on them.  Here is how to find out which ones are installed.


```

dpkg -l | grep libqt4

```

---

### Post by gstefan on 2011-10-15
I have the same issue, but I believe it is not keepassx only, but most QT based applications, since ie. Kadu (instant messaging) has exactly same problem.
Behavior is like this:
1. Program is starting normally and tray icon is created. 
2. When you close it (not minimize) windows is destroyed, but remains icon in tray. 

The problem is, that there is no way to bring this window back, when developer did not put restore function in menu. So in KeePassX we can only forget your password (or shutdown application) in Kadu you can change your status, but no way to bring buddies list visible!
Double click do not work, and right-mouse and left-mouse menus are exactly the same.

Best regards

---

### Post by lucacerone on 2011-10-15
Hi Gamblor01 the output of the command you posted in my case is:
```

dpkg -l | grep libqt4
rc  libqt4-assistant                              4:4.6.2-0ubuntu5.2                         Qt 4 assistant module
ii  libqt4-dbg                                    4:4.7.4-0ubuntu8                           Qt 4 library debugging symbols
ii  libqt4-dbus                                   4:4.7.4-0ubuntu8                           Qt 4 D-Bus module
ii  libqt4-declarative                            4:4.7.4-0ubuntu8                           Qt 4 Declarative module
ii  libqt4-designer                               4:4.7.4-0ubuntu8                           Qt 4 designer module
rc  libqt4-help                                   4:4.7.2-0ubuntu6.1                         Qt 4 help module
ii  libqt4-network                                4:4.7.4-0ubuntu8                           Qt 4 network module
ii  libqt4-opengl                                 4:4.7.4-0ubuntu8                           Qt 4 OpenGL module
ii  libqt4-qt3support                             4:4.7.4-0ubuntu8                           Qt 3 compatibility library for Qt 4
ii  libqt4-script                                 4:4.7.4-0ubuntu8                           Qt 4 script module
rc  libqt4-scripttools                            4:4.7.2-0ubuntu6.1                         Qt 4 script tools module
ii  libqt4-sql                                    4:4.7.4-0ubuntu8                           Qt 4 SQL module
ii  libqt4-sql-mysql                              4:4.7.4-0ubuntu8                           Qt 4 MySQL database driver
ii  libqt4-sql-sqlite                             4:4.7.4-0ubuntu8                           Qt 4 SQLite 3 database driver
ii  libqt4-svg                                    4:4.7.4-0ubuntu8                           Qt 4 SVG module
rc  libqt4-test                                   4:4.7.2-0ubuntu6.1                         Qt 4 test module
ii  libqt4-xml                                    4:4.7.4-0ubuntu8                           Qt 4 XML module
ii  libqt4-xmlpatterns                            4:4.7.4-0ubuntu8                           Qt 4 XML patterns module

```
Are the necessary libraries installed?
Thanks for your help,
Cheers, Luca
P.s. I've tried to uninstall and reinstall and it didn't work.

---

### Post by gamblor01 on 2011-10-15
Looks like your packages are slightly different than the ones that I have installed:

```

$ dpkg -l | grep libqt4 | awk '{print $2}'
libqt4-dbus
libqt4-dbus:i386
libqt4-declarative
libqt4-declarative:i386
libqt4-designer:i386
libqt4-network
libqt4-network:i386
libqt4-opengl
libqt4-opengl:i386
libqt4-qt3support:i386
libqt4-script
libqt4-script:i386
libqt4-scripttools:i386
libqt4-sql
libqt4-sql:i386
libqt4-sql-sqlite
libqt4-svg
libqt4-svg:i386
libqt4-test:i386
libqt4-xml
libqt4-xml:i386
libqt4-xmlpatterns
libqt4-xmlpatterns:i386

```



Anyway, if you install apt-rdepends then you can see the packages that keepassx requires.  Here are the ones that are from libqt4.  I checked and you have all of them:

```

$ sudo apt-rdepends keepassx | grep libqt4 | grep -v "Depends"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt4-xml
libqt4-declarative
libqt4-network
libqt4-dbus
libqt4-script
libqt4-sql
libqt4-xmlpatterns

```


gstefan suggests that the problem is all Qt applications, specifically Kadu has this same problem with the icon in the system tray.  This makes me thing that perhaps everyone having this problem is using the system tray option in KeePassX.  Is that correct?  If you don't know then check your config file.  Depending on the version you have installed, this should be in one of the following locations:

~/.config/keepassx/config.ini
~/.keepassx/config
~/.keepass/config



If I were you, I would set all of the settings related to the system tray and minimizing to false, then try to launch again and see what happens.

```
ShowSysTrayIcon=false
MinimizeToTray=false
MinimizeTray=false
StartMinimized=false
```

---

### Post by gamblor01 on 2011-10-16
Ok I think you can rule out the system tray settings as the culprit.  I just installed 11.10 on my dad's computer because I am tired of cleaning up viruses (may have to reformat yet again there are so many rootkits and so on -- I wouldn't trust entering any personal information on there!).

In any case, I installed 11.10 on a new partition and ran into the same issue.  It's like the program would never properly minimize to the launchbar.  His system happens to have an Intel video card while I have nvidia.  Maybe that is the issue?  Maybe the Intel drivers don't properly handle Qt applications in Unity or something.  Check out what type of card you have like this:

```
lspci -v | grep VGA
```

---

### Post by lucacerone on 2011-10-18
On my laptop it works perfectly...
but on my desktop although I've installed all the dependencies it doesn't show up properly :(

---

### Post by gromoloser on 2011-10-18
I have the same issue. Interestingle Auto-Type is working.

---

### Post by gamblor01 on 2011-10-22
> **lucacerone said:**
> On my laptop it works perfectly...
but on my desktop although I've installed all the dependencies it doesn't show up properly :(

Well when you install it the package manager is going to automatically install all of the dependencies for you, so you will definitely have the dependencies and you shouldn't need to manually install them.

Again, I'm not sure what is causing this but it works fine on some systems but not on others.  It sounds like it's more of an issue with the Qt framework (which keepassx relies on).  This was previously suggested in this thread and it is also suggested here:

[http://ubuntuforums.org/showthread.php?p=11368249](http://ubuntuforums.org/showthread.php?p=11368249)


Perhaps we should open up a bug report with the Qt folks, or maybe on Ubuntu's launchpad?  It's not really clear what is at fault here but it is probably a good idea to get some people that have expertise diagnosing Qt issues involved.  You can file a Qt bug report here:

[https://bugreports.qt.nokia.com//secure/Dashboard.jspa](https://bugreports.qt.nokia.com//secure/Dashboard.jspa)

---

### Post by lucacerone on 2011-10-24
Keepasx worked fine after a fresh install (on a test machine).
I don't have the config files with me now,
but I'll let you know what do they contain when I'm home tonight!

---

### Post by ray field on 2012-04-21
KeepPassX was working fine here under the Precise beta until a couple of days ago -- it kept a working icon in the indicator panel which I could use to quit, for example. now, although it seems to open fine and the application itself is fully-functioning, it won't put up an indicator. when I try to access its Settings, under General(1) the Show system tray icon and all the settings underneath it are now greyed out.

---

### Post by stinkeye on 2012-04-21
Same here.
No indicator icon.
I only used to use this to quit the app because the 
keepassx window used to disappear after performing an autotype.
It now minimizes properly to the launcher so no need anymore.

---

### Post by bobzr on 2012-05-25
Same problem in 12.04. KeePassX doesn't show a launcher icon when opened. A bug #1002874 has been reported:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1002874](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1002874)

I press Win+W to get back an opened keepassx window.

Does anybody know a better workaround?

---

