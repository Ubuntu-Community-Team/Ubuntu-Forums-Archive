---
title: "[SOLVED] Cannot Open Screenlets Manager"
date: 2008-03-04
forum: Desktop Effects &amp; Customization
---

### Post by Anthony M on 2008-03-04
I had screenlets working just a few days ago, but then needed to perform a fresh install of Gutsy. Now I install Screenlets from Synaptic and the installation goes without errors, but Screenlets will _not_  launch.

When I go to System>Preferences>Screenlets, it returns the error:

```
Failed to execute child process "/usr/local/share/screenlets-manager/screenlets-manager.py" (No such file or directory)
```

I have tried installing through Synaptic and from source, no avail...

Why is screenlets installing but not creating this file? It is not even creating the screenlets-manager directory...

Thanks!

---

### Post by plun on 2008-03-04
Please test the new version

[http://www.getdeb.net/release.php?id=2128](http://www.getdeb.net/release.php?id=2128)

The new version is only within Ubuntus repo for Hardy, the old
one ver 0.0.10 is backported to Gutsy (but its really buggy as you see)
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=screenlets](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=screenlets)


.

---

### Post by Anthony M on 2008-03-04
> **plun said:**
> Please test the new version

[http://www.getdeb.net/release.php?id=2128](http://www.getdeb.net/release.php?id=2128)

The new version is only within Ubuntus repo for Hardy, the old
one ver 0.0.10 is backported to Gutsy (but its really buggy as you see)
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=screenlets](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=screenlets)


.

Thanks for the help but that version is giving me the same error.

FWIW, I cannot get gDesklets working either. I have them installed, but cannot launch them....

Could these be related?

---

### Post by plun on 2008-03-04
Nope. I don't think they are related

Start the terminal and this command

```
screenlets-manager
```

The manager should start and a little screenlets icon in the tray

Post output if it fails

---

### Post by Anthony M on 2008-03-04
That worked! For whatever reason running it from the terminal works fine. Now I need to figure out how to make it work from Preferences>Screenlets.
```
anthony@DFQJPC61:~$ screenlets-manager
It looks like you are running gnome
/home/anthony/.config/autostart/Screenlets Daemon.desktop
/home/anthony/.config/autostart/screenlets-daemon.desktop
False
Starter already exists.
DAEMON FOUND!

```

Do I just need to change the Launcher command? 

Thank you!

On Edit: That was easy. I just put the command "screenlet-manager" in the Menu Launcher.

---

### Post by plun on 2008-03-04
Well, "automagic" things happens when you run screenlets-manager. :)

- The screenlets-tray icon is easily used with a left click for the manager or a **right click** for commands/settings

- The tray icon start is also within Menu System>Prefs >Sessions so it will
autostart every time...

Please also see settings within the manager, Start/Stop etc...

The manager supports drag & drop so its just to download new Screenlets and drop the
file for easy  install

[http://gnome-look.org/index.php?xcontentmode=6700](http://gnome-look.org/index.php?xcontentmode=6700)


Have Fun  :)

---

### Post by Anthony M on 2008-03-04
It actually worked too good!

Now, everytime I start the manager, it keeps starting another manager, and another, and another.

Until I log out, I have Screenlet Managers keep popping open about once a second!

**Edit:** Once again, another simple fix! Upon running screenlets-manager in terminal (As a n00b, I am really starting to appreciate the terminal), I noticed Pandora Screenlet was erroring. I uninstalled that screenlet and all is well now. 

Thanks again!

---

