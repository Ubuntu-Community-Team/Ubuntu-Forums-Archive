---
title: "KDM/GDM takes XFCE hostage"
date: 2006-01-04
forum: Desktop Environments
---

### Post by rhipwell on 2006-01-04
Hi everyone,

I recently decided to make a switch to XFCE and have found a bit of a problem. When using KDM or GDM as the login manager it takes over my XFCE session. Essentially what happens is I cannot change my background and right clicking on the desktop does not bring up the menu. This effect has occured on both the users on my system. Anyone have any ideas how to remedy this? Thanks

Turns out that my session is pooched....still not sure what happened to it, I am using WDM now...I'll update when I test extensivly. Thanks

---

### Post by Clazzy on 2006-01-04
It sounds like Nautilus has been loaded in XFCE. Try loading a console and typing:
sudo killall nautilus
If you load Nautilus, the shortcut must have --no-desktop tagged on the end.

---

### Post by rhipwell on 2006-01-04
[QUOTE=Clazzy]It sounds like Nautilus has been loaded in XFCE. Try loading a console and typing:
sudo killall nautilus
If you load Nautilus, the shortcut must have --no-desktop tagged on the end.[/QUOTE]


Would this also hold true to konquerer?

---

### Post by Clazzy on 2006-01-04
No, Konqueror won't take over your desktop like Nautilus does.

---

### Post by rhipwell on 2006-01-05
[QUOTE=Clazzy]No, Konqueror won't take over your desktop like Nautilus does.[/QUOTE]

Thats good to know, however my 'default' session is still having issues wheras my 'test' session is working fine. So something within the session itself appears to have problems. 

my xfce4-session.rc is as follows: 

[General]
SessionName=Default
SaveOnExit=true
AutoSave=false
PromptOnLogout=true
DisableTcp=true

[Splash Screen]
Engine=balou

[Compatibility]
LaunchGnome=false
LaunchKDE=false

[Chooser]
AlwaysDisplay=true

that is apparently only for my default session...I can't find the test one. Any ideas where I can look ( I found that in ~/.config/xfce4-session )

---

