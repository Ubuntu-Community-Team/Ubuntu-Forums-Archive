---
title: "remove gnome extension"
date: 2022-01-01
forum: Desktop Environments
---

### Post by jgw on 2022-01-01
I am having a problem with gnome extensions.  I have tried to remove some of them but they just coming back.  I started to mess with stuff and cleverly moved my top bar to the bottom bar which, in turn, hides the dock.  This happened with something called Dash to Panel.  I told it to go to the bottom, then got a square with "error" and now it just lays there  I have also tried to log into the extension page but that made no difference.  I suspect my best move would be to remove all extensions and start over but I can't even get rid of one of those!

Thoughts?

---

### Post by KBar on 2022-01-01
First, we need to identify which extensions you installed and how exactly you installed them. Run the following and paste its output:
```
dpkg -l | grep 'gnome-shell-extension'
```

---

### Post by jgw on 2022-01-01
First, thanks for the reply!

First, I have been messing around.  This time it seems that if I just turn them off they stay off!  I tried this before and it didn't work.  So, regardless of the outcome things are not as bad as I had thought.
Below are all my extensions and I currently have most of them turned off.  The strange thing is that I can delete them, if they have a green gear icon I can click on that extension, get an install offer.  Then I can install and I will have an 'x' at the end which will allow me to delete.  It keeps track and gives me a list of the deleted, etc.  The problem is that when I leave, and go back in everything is back.  I did note that its says that I will need superuser status to actually get rid of them but I haven't gone with that one yet.  I am considering going into the terminal, do a "sudo -s" and then run firefox and see what happens but, I suspect, that's unlikely to do the trick.

```
kg -l | grep 'gnome-shell-extension'
ii  gnome-shell-extension-appindicator            33.1-0ubuntu0.20.04.2                 all          AppIndicator/KStatusNotifierItem support for GNOME Shell
ii  gnome-shell-extension-arc-menu                45-1                                  all          shell extension designed to replace the standard menu found in GNOME
ii  gnome-shell-extension-autohidetopbar          20200322-1                            all          GNOME shell automatic topbar hider
ii  gnome-shell-extension-bluetooth-quick-connect 10-3                                  all          GNOME Shell extension to connect paired Bluetooth devices
ii  gnome-shell-extension-caffeine                35-2                                  all          GNOME Shell extension to keep your computer awake
ii  gnome-shell-extension-dash-to-panel           31-1ubuntu20.04.1                     all          combines the dash and the GNOME main panel into a single panel
ii  gnome-shell-extension-desktop-icons           20.04.0-3~ubuntu20.04.6               all          desktop icon support for GNOME Shell
ii  gnome-shell-extension-disconnect-wifi         21-1                                  all          disconnect Wi-Fi extension for GNOME shell
ii  gnome-shell-extension-draw-on-your-screen     6-1                                   all          start drawing on your screen and save your beatiful work in a screenshot
ii  gnome-shell-extension-gamemode                4-2                                   all          gnome-shell extension that monitors the current status of gamemode
ii  gnome-shell-extension-gsconnect               20-0ubuntu1                           all          KDE Connect implementation for GNOME Shell
ii  gnome-shell-extension-gsconnect-browsers      20-0ubuntu1                           all          Browser support of KDE Connect implementation for GNOME Shell
ii  gnome-shell-extension-hard-disk-led           19-1                                  all          Shows harddisk activity (IO speed read/write and LED) in GNOME Shell
ii  gnome-shell-extension-hide-activities         0.00~git20131024.1.6574986-2          all          GNOME shell extension that hides the activities button
ii  gnome-shell-extension-hide-veth               1.0.2-1                               all          hides veth devices typically used by docker and lxc
ii  gnome-shell-extension-hijra                   1.0-1                                 all          Hijri Islamic Calendar GNOME shell extension
ii  gnome-shell-extension-impatience              0.4.5-4                               all          speed up the gnome-shell animation speed
ii  gnome-shell-extension-kimpanel                0~20200310.45dc4e4-1                  all          KDE kimpanel protocol extension for GNOME shell
ii  gnome-shell-extension-log-out-button          1.0.8-1                               all          Adds a log out button to the system action list in GNOME Shell
ii  gnome-shell-extension-move-clock              1.01-2                                all          move clock extension for GNOME shell
ii  gnome-shell-extension-multi-monitors          19-1                                  all          Better support for additional monitors in GNOME shell
ii  gnome-shell-extension-no-annoyance            0+20170928-f21d09a-2                  all          removes GNOME 'Window is ready' notifications
ii  gnome-shell-extension-onboard                 1.4.1-2ubuntu7                        all          GNOME Shell extension for the on-screen keyboard Onboard
ii  gnome-shell-extension-pixelsaver              1.20-1                                all          pixel saver extension for GNOME shell
ii  gnome-shell-extension-prefs                   3.36.9-0ubuntu0.20.04.2               amd64        tool to enable / disable GNOME Shell extensions
ii  gnome-shell-extension-redshift                3.20.1-2                              all          redshift extension for GNOME Shell
ii  gnome-shell-extension-remove-dropdown-arrows  13-1                                  all          removes drop down arrows from panel on GNOME shell
ii  gnome-shell-extension-shortcuts               1.1.1-1                               all          Creates a shortcuts help pop-up in GNOME Shell
ii  gnome-shell-extension-show-ip                 8-5                                   all          Shows the current private or public IP address
ii  gnome-shell-extension-suspend-button          0~git20191005-1                       all          Gnome-shell extension to modify the suspend/shutdown buttons
ii  gnome-shell-extension-system-monitor          38+git20200414-32cc79e-1              all          Display system information in GNOME Shell status bar
ii  gnome-shell-extension-tilix-dropdown          7-1                                   all          launch tilix in quake-mode from gnome-shell
ii  gnome-shell-extension-tilix-shortcut          1.0.1-2                               all          Adds easy to use configurable keyboard shortcut for tilix
ii  gnome-shell-extension-top-icons-plus          22-5                                  all          GNOME Shell extension to move system tray icons to top bar
ii  gnome-shell-extension-trash                   0.2.0-git20161122.ad29112-2           all          trash applet for GNOME shell
ii  gnome-shell-extension-ubuntu-dock             68ubuntu1~20.04.1                     all          Ubuntu Dock for GNOME Shell
ii  gnome-shell-extension-weather                 0~20170402.git34506a6-2               all          weather extension for GNOME Shell
ii  gnome-shell-extension-workspaces-to-dock      52+git20200318-1                      all          additional options for GNOME workspace switcher
ii  gnome-shell-extension-xrdesktop               0.14.0-2                              all          GNOME Shell extension to control XR desktop.
ii  gnome-shell-extensions                        3.36.1-1                              all          Extensions to extend functionality of GNOME Shell
ii  gnome-shell-extensions-gpaste                 3.36.3-1                              all          GPaste extension for GNOME Shell
greg@gregdown:~$ 

```

---

### Post by KBar on 2022-01-02
Woah, that's a lot of extensions! Are you sure you want or even need all of them? They slow your system down by a lot. 

Moreover, it seems that they were installed via the *Extensions* app. I don't think it provides removal as I haven't used GNOME in a long while. However, you can always remove anything from the shell.
[LIST=1]
[*]Open a text editor and put its window side by side with the list of extensions you got with [FONT=courier new]dpkg -l[/FONT].
[*]Copy and paste the names of the ones you want to remove, separating each name with a space or a newline, and save the file.
[*]Go back to the shell and run the following, replacing _the-path-to-that-file_ with the appropriate file name:```
apt --simulate purge $(cat the-path-to-that-file)
```This will run **apt** in simulated mode, which you can always use to double-check which packages are to be removed.
[*]If you're satisfied with the list, run the following to purge the packages found in the list:```
sudo apt purge $(cat the_path_to_that_file)
```
[*]Log out and log back in for the changes to take effect.
[/LIST]

---

### Post by jgw on 2022-01-02
Thanks for the reply!

I can try your suggestions although I tend to believe it will do no good.  My reason for that is because I delete them but, after I reboot, they are back like bad pennies.  I have, pretty much, decided that just disabling those I don't want is the way to go as that sticks.  Oh, and I am really lazy!  

Thanks again!

---

### Post by kurt18947 on 2022-01-03
Have you tried this from the extensions.gnome.org web site? I don't have anywhere near as many extensions installed and would hesitate to do so; they can conflict. I've been able to deactivate and remove using the extensions web site and I don't need sudo, extensions are per user AFAIK and nothing to do with system.

---

### Post by jgw on 2022-01-04
I have been to the extensions.gnome.org directly and also through firefox.  In both cases whatever I delete returns next time I check.  its a very strange thing.  However (again), I have found that if I just turn them off they stay off and I can deal with that so I am just going to leave them alone.  Everytime I start messing with them I tend to get into trouble.  When I turn them off there are some that I can't even turn off but there is only one or two of those so I live with them.  I, obviously, have some kind of problem but its not deadly and I rarely actually go into the extensions, other than to update them when it start to bug me to do that.  

Anyway, thanks for the replies and the help.  I think I am just going to mark this as solved and move on.  I really wished there was a way to mark them a waste of time instead.  This, in the end was that, if nothing else.  Maybe, instead, a place to put failed fixes that don't count.

---

### Post by kurt18947 on 2022-01-04
That is odd. When I've used the web site and clicked on the red 'X' to remove that extension does not reappear. I'm glad you're able to live with what you have. Perhaps if/when you reinstall for a new version or something the irritating behavior will not reappear. I've FUBARed my share of installs, it's not the end of the world.

---

### Post by jgw on 2022-01-06
I have been messing with computers for over 60 years and have found its sometimes easier to just deal with something rather than fix it.  Getting old now and really not up to what I used to be able to do so I live with stuff that doesn't shut me down. 

Thank you for the reply and the help.

---

