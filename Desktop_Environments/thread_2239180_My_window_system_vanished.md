---
title: "My window system vanished"
date: 2014-08-12
forum: Desktop Environments
---

### Post by Carllacan on 2014-08-12
Hi.

I'm using Ubuntu 14.04 on an Asus K52J. I have been having [some issues with Unity]("http://ubuntuforums.org/showthread.php?t=2237261") and I tried to solve them  restoring the whole Compiz configuration to its defaults settings, via the compiz configuration GUI. After I did it I lost my Unity launcher, my Desktop panel, and pretty much my whole desktop environment. A restart doesn't solve it. Any idea about how can I solve this?

Thank you for your time.

---

### Post by grahammechanical on 2014-08-12
Did you happen to disable the Unity plugin? That will do it. The ability to disable the Unity plugin was removed from Compiz Configuration Settings Manager (CCSM) but this function has now been restored and we are warned about the power of CCSM.

It might be possible to launch CCSM from a terminal Ctrl+Alt+T with this command

```
compizconfig-settings-manager
```

I do not have CCSM installed so I have not tested that command. But that is the command name of CCSM. Other possible useful commands.

Resets Compiz (Not the CCSM)

```
dconf reset -f /org/compiz/
```

Restarts Unity

```
setsid unity
```

Regards.

---

