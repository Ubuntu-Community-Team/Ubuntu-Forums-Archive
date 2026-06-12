---
title: "System -&gt; Preferences -&gt; Sessions -&gt; Startup Program -&gt; Add."
date: 2006-12-15
forum: Desktop Environments
---

### Post by p2cd3 on 2006-12-15
I am still trying to setup conky at startup

I keep seeing answers for startup as: System -> Preferences -> Sessions -> Startup Program -> Add.

Am I missing something or doing someting wrong?

This is the listing for my System>
adept manager ......
Automatix Graphical.......
kCron Task scheduler
keep Backup System
KinfoCentre info centre
Konsole Terminal Program
KSysGuard Performance Monitor
KSystemLog System Logs Viewer
Kubuntu Device Database
Language Support
Synaptic Package Manager

These are the programs listed under System

---

### Post by meng on 2006-12-15
System > Preferences ...(etc) applies to GNOME, not KDE. I can't recall where in the KDE tree this sessions thing is, have you looked in Configuration or in KDE Control Center?

---

### Post by p2cd3 on 2006-12-15
In kubuntu I have System Settings > Advanced > System Services, but cannot find how to add conky to start at boot up

---

### Post by ajgreeny on 2006-12-15
Add a link to the ~/.kde/Autostart folder and that should do it.

---

### Post by p2cd3 on 2006-12-15
The how-to for conky says:
Also, to get Conky to autostart in Kubuntu, you need to add a link to the bin file (in /usr/bin) to 

~/.kde/Autostart

As you said, but not sure what the link will say in /usr/bin

---

### Post by ajgreeny on 2006-12-15
I don't know anything about conky, but have a look in */user/bin* for something with conky in the name, or more simply just use the same command you use in a terminal, or the same command that is in the KDE menu for conky (probably just "conky", without the need for the pathway to be used.

---

