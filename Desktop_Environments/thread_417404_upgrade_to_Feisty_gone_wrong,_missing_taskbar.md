---
title: "upgrade to Feisty gone wrong, missing taskbar"
date: 2007-04-21
forum: Desktop Environments
---

### Post by yurtos on 2007-04-21
hey folks,
i have upgraded to Feisty (i think), things seemed ok before i shut down my machine. after a few reboots im missing KDE menu and things on the right hand side like clock, other desktops shotcuts and so on.
here is the screenshot of my desktop right now.
[link]("http://img133.imageshack.us/img133/4485/snapshot8yw5.png")

please advise where to start troubleshooting this issue.

p.s. my boot log here:
```
yurtos@rs-intel:~$ cat /var/log/boot
Apr 21 14:16:05 rcS:  * Reading files needed to boot...                  [ ok ]
Apr 21 14:16:06 rcS:  * Setting preliminary keymap...                    [ ok ]
Apr 21 14:16:06 rcS:  * Starting basic networking...                     [ ok ]
Apr 21 14:16:06 rcS:  * Starting kernel event manager...                 [ ok ]
Apr 21 14:16:07 rcS:  * Loading hardware drivers...                      [ ok ]
Apr 21 14:16:07 rcS:  * Loading manual drivers...                        [ ok ]
Apr 21 14:16:08 rcS:  * Mounting local filesystems...                           mount: No medium found
Apr 21 14:16:09 rcS:                                                     [fail]
Apr 21 14:16:09 rcS:  * Activating swapfile swap...                      [ ok ]
Apr 21 14:16:00 rcS:  * Configuring network interfaces...                [ ok ]
Apr 21 14:16:01 rcS:  * Setting up console keymap...                     [ ok ]
Apr 21 14:16:01 rc2:  * Loading ACPI modules...                          [ ok ]
Apr 21 14:16:01 rc2:  * Starting ACPI services...                        [ ok ]
Apr 21 14:16:12 rc2:  * Starting system log...                           [ ok ]
Apr 21 14:16:12 rc2:  * Starting kernel log...                           [ ok ]
Apr 21 14:16:12 rc2: Starting K Display Manager: kdm.
Apr 21 14:16:12 rc2:  * Starting Common Unix Printing System: cupsd      [ ok ]
Apr 21 14:16:13 rc2:  * Starting HP Linux Printing and Imaging System    [ ok ]
Apr 21 14:16:13 rc2:  * /etc/rc2.d/S19mysql: ERROR: The partition with /var/lib/mysql is too full!
Apr 21 14:16:13 rc2:  * Starting apt index watcher apt-index-watcher     [ ok ]
Apr 21 14:16:13 rc2:  * Starting system message bus dbus                 [ ok ]
Apr 21 14:16:17 rc2:  * Starting Hardware abstraction layer hald         [ ok ]
Apr 21 14:16:17 rc2:  * Starting LPRNG printer spooler lpd               [ ok ]
Apr 21 14:16:18 rc2:  * Starting Bluetooth services                      [ ok ]
Apr 21 14:16:24 rc2: Starting Win4Lin Pro  *   [done]
Apr 21 14:16:24 rc2:  * Starting anac(h)ronistic cron: anacron           [ ok ]
Apr 21 14:16:24 rc2:  * Starting periodic command scheduler...           [ ok ]
Apr 21 14:16:25 rc2:  * Starting apache 2.0 web server...                [ ok ]
Apr 21 14:16:25 rc2:  * Checking battery state...                        [ ok ]
Apr 21 14:16:25 rc2:  * Running local boot scripts (/etc/rc.local)       [ ok ]
```

---

### Post by SOULRiDER on 2007-04-21
Press alt + f2 and run 'kicker'

---

### Post by yurtos on 2007-04-21
in terminal it gives me an error that its already running. i tried killing kicker and starting again but my problem remains unsolved. tried restarting kicker after fresh reboot, nothing... taskbar looks the same, still missing KDE menu, clock and other stuff.

---

### Post by SOULRiDER on 2007-04-22
If your taskbar is there, right click it and then hit "Add Applet to panel" there you can select clock, k menu, application list etc. etc.

---

### Post by yurtos on 2007-04-22
you are right, silly me. put everything back in place.
all sorted now.

thank you

---

