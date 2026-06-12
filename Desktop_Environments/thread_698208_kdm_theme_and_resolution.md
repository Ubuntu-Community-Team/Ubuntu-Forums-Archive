---
title: "kdm theme and resolution"
date: 2008-02-16
forum: Desktop Environments
---

### Post by draeath on 2008-02-16
I have two issues. I'm on Kubuntu 7.10 amd64

First issue: I can't seem to get KDM to use anything but the default Kubuntu theme. This theme is fine, except I want the userlist removed for security reasons. I would *prefer* to have normal full control as per the KDE Control Center's "Login Manager" applet provides (which seems to be getting ignored)

I tried commenting out the */etc/kde3/kdm/kdmrc* line:  ```
Theme=@@@ToBeReplacedByDesktopBase@@@
```
This had no effect, so I reverted the change. No other changes were made in /etc/kde3/


Second issue: KDM (or x.org at the moment KDM is awaiting me to log in) is using a resolution that I can't use, and so does the scrolly-virtual-desktop thing. I've removed all resolutions above 1280x1024 in my X config, including both the Screen config and the monitor modelines... but KDM still goes ahead and tries to use the 14xx-something resolution that I know for a fact the monitor does not support (and the monitor make/model is specified, as well as vertical/horizontal scan rates).

Here is my [COLOR="Blue"]_[x.org configuration]("http://pastebin.com/f37402fee")_[/COLOR].

Any help you could provide would be appreciated.

---

### Post by samwyse on 2008-02-16
The settings in the control center start working after a reboot or restarting KDM in a way I haven't really bothered to figure out.

Kubuntu sets a virtual resolution for KDM. You can try adding a # in front of the "Virtual 1400 1050" line. I have just left it alone, because I get problems with the desktop resolution using proprietary drivers if I comment the line.

---

### Post by oobuntoo on 2008-02-16
I have found a solution to changing kdm theme that sort of work. I installed kdm theme manager version 1.2.2 from one of the repos using Synaptic. I can install and change themes with kdm theme manager, but not able to uninstall themes with it; it crashed when I tried. Once installed, kdm theme manager appears in  kcontrol, under System Administration.

BUT, before it works, you need to delete file(s) under /etc/default/kdm.d directory. I can't remember exactly what it's/they're called; something like kubuntudefault.xxx or defaultsettings.xxx. Just delete them all or rename/move them somewhere else.

You may also have to edit /etc/kde3/kdm/kdmrc file as follow:

remove the leading # from #UseTheme=true"

At least, this is how got it to work. I still don't know why I can't uninstall themes with kdm theme manager, but you can alway manually delete themes you don't want by deleting folders from /usr/share/apps/kdm/themes directory

---

### Post by draeath on 2008-02-16
I'll be sure to test these suggestions out when I have time. Thanks!

BTW, is there a launchpad bug for this issue?

---

