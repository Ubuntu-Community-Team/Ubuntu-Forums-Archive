---
title: "Ubuntu Netbook Remix: gnome-panel and nautilus don't appear"
date: 2009-04-10
forum: Desktop Environments
---

### Post by dtech on 2009-04-10
Hi,

I recently installed Ubuntu Netbook Remix (UNR) on my Asus Eee PC.
at first it worked well, expect for wireless, but after some configuration it worked.

After I updated however, when I restarted the panel and window managers didn't work: there was a semi-black bar on top and when I started something with the launcher it had not borders and couldn't be moved.

When I switched back and forth to classic and again to netbook mode everything worked perfectly.

It also works fine if I type the following two commands into the terminal:
```

(gnome-panel &)
(metacity &)

```
which are designed to run (and do run) gnome-panel and metacity seperate from the console.

My question is: how do I fix this so I don't have to do that all the time?

I have also made a bash script which will do it every reboot, but I find that a rather ugly solution.

```

#!/bin/sh

# These dissapear, I'm trying to restore them

# Check if a nautilus process exists
if [ `pgrep -c metacity` = 0 ]; then	
	(nautilus &) # Start nautilus
fi

# Check if a gnome-panel process exists
if [ `pgrep -c gnome-panel` = 0 ]; then
	(gnome-panel &) # Start gnome-panel
fi

```

---

### Post by elchi3001 on 2009-04-10
i have the same problem
usin gnome-panel brings back the panels and after switching from the normal gnome desktop to the netbook desktop i get this error message:
> Beim Laden oder Speichern der Konfiguration von netbook-launcher ist ein Fehler aufgetreten. Einige Ihrer Konfigurationseinstellungen könnten nicht richtig funktionieren.  
Der Konfigurationsserver konnte nicht kontaktiert werden; mögliche Fehlerquellen sind, dass TCP/IP für ORBit nicht aktiviert ist oder auf Grund eines Systemabsturzes alte NFS-Sperren gesetzt sind. Unter [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) erhalten Sie weitere Informationen (Details –  1: Es konnte keine Nachricht an den GConf-Dämon gesendet werden: Message did not receive a reply (timeout by message bus))
Der Konfigurationsserver konnte nicht kontaktiert werden; mögliche Fehlerquellen sind, dass TCP/IP für ORBit nicht aktiviert ist oder auf Grund eines Systemabsturzes alte NFS-Sperren gesetzt sind. Unter [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) erhalten Sie weitere Informationen (Details –  1: Es konnte keine Nachricht an den GConf-Dämon gesendet werden: Message did not receive a reply (timeout by message bus))

it says that it was unable to save some configuration relatet to the netbook-launcher because the gconf-daemon is not answering.

---

### Post by elchi3001 on 2009-04-10
i just managed to fix this.
i realized the problem was only with one user account, so the problem was in my home directory, here i renamed the hidden files named .gconf and .gconfd. relogged and the panel showed up normaly.

---

### Post by dtech on 2009-04-11
That indeed works.

I recommend backup up your config and later writing over the config of some apps if you want to keep the configuration for some apps (e.g. gedit, which I heavily customized)
**Keep in mind that almost all of your gnome configuration will be lost, including you (wireless) networks and shortcuts**

Run this in a terminal (after closing all your apps):
```

cd ~
mv .gconf .gconf_backup
mv .gconfd .gconfd_backup
sudo reboot

```

When the computer is rebooted, go to .gconf_backup and copy back to .gconf the application settings you want to restore.

---

### Post by ahbart on 2009-04-15
I had the same problem and created a bug report in launchpad. It might help if you could confirm this bug.
have a look here: [link](https://bugs.launchpad.net/netbook-remix-launcher/+bug/361625)

---

### Post by dtech on 2009-04-15
Hi ahbart,

I'm not confirming the bug, since this is a slightly different problem (with the same solution, so the underlying cause might be the same). However, since it happened with you after you removed netboox-remix (while I still had it installed and wanted to keep it)

---

### Post by ahbart on 2009-04-15
Well, it doesn't keep me out of my sleep. ;)

---

### Post by njpatel on 2009-04-16
This a bug in the desktop-switcher package ([https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519)), which I'm trying to fix and get uploaded to Jaunty before release.

To fix the issue you have currently (gnome-panel and/or windowmanager not starting), please run the following command depending on which mode your currently running in:

If in Netbook-mode, should execute:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]

If in Classic mode:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]

I have updated desktop-switcher .debs available in that bug for which I am looking for testers (I would appreciate feedback on that bug). Once you've run the above commands, you can install the latest deb from that bug and hopefully further switches will work without issue.

Thanks and sorry for desktop-switcher screwing up :)

-- Neil

---

### Post by redDEADresolve on 2009-04-27
> **njpatel said:**
> This a bug in the desktop-switcher package ([https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519)), which I'm trying to fix and get uploaded to Jaunty before release.

To fix the issue you have currently (gnome-panel and/or windowmanager not starting), please run the following command depending on which mode your currently running in:

If in Netbook-mode, should execute:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]

If in Classic mode:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]

I have updated desktop-switcher .debs available in that bug for which I am looking for testers (I would appreciate feedback on that bug). Once you've run the above commands, you can install the latest deb from that bug and hopefully further switches will work without issue.

Thanks and sorry for desktop-switcher screwing up :)

-- Neil

Where is that .deb?

---

### Post by ahbart on 2009-04-27
Just follow the url above.

---

### Post by Ralphthedog on 2009-05-02
> **njpatel said:**
> This a bug in the desktop-switcher package ([https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519)), which I'm trying to fix and get uploaded to Jaunty before release.

To fix the issue you have currently (gnome-panel and/or windowmanager not starting), please run the following command depending on which mode your currently running in:

If in Netbook-mode, should execute:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]

If in Classic mode:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]

I have updated desktop-switcher .debs available in that bug for which I am looking for testers (I would appreciate feedback on that bug). Once you've run the above commands, you can install the latest deb from that bug and hopefully further switches will work without issue.

-- Neil

After going through this solution (and a few others...) I'm still missing my two menus on the panel in my Epc900's classic desktop.

Got/installed the desktop-switcher_0.4.6_i386.deb

I've tried deleting all my config stuff for gnome to no avail...

Does anyone have an idea?

---

### Post by ahbart on 2009-05-02
What do you mean by two menu's? If you deleted all the config's than everything has been disappeared. That makes sense. 
I assume that only an install of the new desktop-switcher would have done the trick for you.
You can get your menu's back by right clicking on the panel en add the applets from there.

---

### Post by Ralphthedog on 2009-05-02
Thanks for the reply ahbart, I mean the three (not two...duh!) menus top left - application, places, system.

I have the most recent desktop switcher installed -  been fiddling about with the desktop switcher problem following smarter peoples leads, but this has me stumped.

---

### Post by gregpritchard on 2010-01-28
> **dtech said:**
> That indeed works.

I recommend backup up your config and later writing over the config of some apps if you want to keep the configuration for some apps (e.g. gedit, which I heavily customized)
**Keep in mind that almost all of your gnome configuration will be lost, including you (wireless) networks and shortcuts**

Run this in a terminal (after closing all your apps):
```

cd ~
mv .gconf .gconf_backup
mv .gconfd .gconfd_backup
sudo reboot

```When the computer is rebooted, go to .gconf_backup and copy back to .gconf the application settings you want to restore.

Nailed it. Sorted now

---

