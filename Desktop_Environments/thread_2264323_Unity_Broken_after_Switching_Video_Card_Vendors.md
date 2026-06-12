---
title: "Unity Broken after Switching Video Card Vendors"
date: 2015-02-06
forum: Desktop Environments
---

### Post by KoopaTroopa on 2015-02-06
Hello.

So I usually use an AMD radeon card but needed to test out a Nvidia card momentarily. Once I was done I un-installed the nvidia drivers (passing --uninstall to the install script) and put my original card back in. I installed catalyst it via the .run file downloaded from their website. I have previously installed the same driver via the same method and it worked fine in the past. Unity only shows the desktop wallpaper and my files on it. I tried 'dconf reset -f /org/compiz;setsid unity' and checked compiz is enabled in ccsm, which it is. When switching to a different tty I get the message "failed to parse arguments. Unable to open display".

Currently I am able to login to gnome fall back using metacity. Running unity via terminal results in
```
ash@PalletTown:~$ unity --replaceunity-panel-service stop/waiting
unity-panel-service start/running, process 9995
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
```

---

