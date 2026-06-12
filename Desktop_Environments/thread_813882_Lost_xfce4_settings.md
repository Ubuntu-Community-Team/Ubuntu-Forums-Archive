---
title: "Lost xfce4 settings"
date: 2008-05-31
forum: Desktop Environments
---

### Post by FreeFull on 2008-05-31
Yesterday ( 30 may 2008 ) I have installed many games and filled up my partition. I have shut my laptop down. I have booted up today and xfce4-panel was acting strange. The "Applications" button changed to "Xfce Menu". I lost all the "activators" (I don't know the English name, I'm have a Polish locale).
I removed all games I didn't really needed, logged out, and logged back in. The xfce4-panel still is the same, and I lost other xfce4 settings. XChat lost the server list. The desktop and the xfce4-menu fortunately didn't change. Can anybody help please?

---

### Post by paulphillips on 2008-05-31
Do the system logs say anything useful (System->System Log)?

---

### Post by FreeFull on 2008-05-31
I don't seem to have the system log thing in the system menu.

---

### Post by paulphillips on 2008-05-31
Sorry - System->Administration->System Log

---

### Post by FreeFull on 2008-05-31
Em, I'm running Xubuntu, not Ubuntu. The interface is a bit different. I also don't have the system log thing anywhere? Should I just go to the system logs in thunar and post them directly? Which ones?

---

### Post by paulphillips on 2008-05-31
open a terminal window (don't know kubuntu app name) and inspect logs in /var/log

---

### Post by FreeFull on 2008-05-31
Nothing abnormal in the logs... it seems that I just lost certain portions of xfce4 config. Oh well. I will just have to configure it all again. Thanks anyway.

---

### Post by mksql on 2008-05-31
> **FreeFull said:**
> Yesterday ( 30 may 2008 ) I have installed many games and filled up my partition. I have shut my laptop down. I have booted up today and xfce4-panel was acting strange. The "Applications" button changed to "Xfce Menu". I lost all the "activators" (I don't know the English name, I'm have a Polish locale).

I am having a nearly identical problem:

[http://ubuntuforums.org/showthread.php?t=814534](http://ubuntuforums.org/showthread.php?t=814534)

---

### Post by morgengenuss on 2008-06-01
@FreeFull: i once had this problem, because my partition was full (with full i mean: to the rim, there was no free space at all) and i didn't notice. when i rebooted, the configs were loaded correctly but on the next login (or maybe even during that session already) everything was gone, because the system tried to save the configs but since there was no space it couldn't. so it just corrupted all the settings (in quite every programme). i had to redo quite all the configuration, i fear there is no way around that. (maybe for the future back up all the configuration in your $HOME, it really doesn't take that much space.)

---

