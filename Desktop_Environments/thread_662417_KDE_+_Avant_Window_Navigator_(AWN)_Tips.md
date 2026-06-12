---
title: "KDE + Avant Window Navigator (AWN) Tips"
date: 2008-01-08
forum: Desktop Environments
---

### Post by fatbuttlarry on 2008-01-08
[img]http://img265.imageshack.us/img265/1742/testsq6.png[/img]

For the [avant-window-navigator]("https://launchpad.net/awn") fans, I've noticed it doesn't work well with [KDE]("http://www.kde.org/"). (They're working on a desktop-independent version, but it still has a long way to come).

Basically, avant-window-navigator was built to work with gnome + compiz.  If you don't have gnome, a lot of stuff won't work in Kubuntu.  (You'll notice during install it requires quite a few gnome dependencies)

Here are are few tricks I've learned help using it with KDE:

**Quit/Logout Button:**
I've noticed this crashes Emerald (which is needed with KDE + compiz).  The KDE logout, does not crash Emerald.  Here's what I did:
[LIST=1]
[*]Remove the Quit/Logout Applet
[*]Save [this icon]("http://img212.imageshack.us/img212/1959/logoutfy3.png") somewhere
[img]http://img212.imageshack.us/img212/1959/logoutfy3.png[/img]
[COLOR="Blue"][SIZE="1"]mirror: [1](http://img212.imageshack.us/img212/8733/logout1gn8.png) [2](http://img212.imageshack.us/img212/6794/logout2bz1.png)[/SIZE][/COLOR]
[*]Make a new Launcher that launches this:
```
dcop kdesktop KDesktopIface logout
```
(If you are confused, try K-Menu >> Settings >> AWN Manager)

[/LIST]
[B]
Fixing the trash bin:[/B]
[COLOR="Blue"]See link:[ konqueror in gnome](http://ubuntuforums.org/showpost.php?p=4009511&postcount=23)[/COLOR]

**[COLOR="Red"]**Please note, this trash bin work-around is a dirty hack.  It replaces the nautilus executable, which is not recommended for beginners, or anyone who plans to use the gnome desktop.  The script can be modified to work with both KDE and nautilus, but you'll need to do some scripting homework first.[/COLOR]**



-Tres

---

