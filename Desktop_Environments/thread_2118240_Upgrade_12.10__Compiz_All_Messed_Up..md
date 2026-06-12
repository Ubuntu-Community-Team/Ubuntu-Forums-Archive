---
title: "Upgrade 12.10  Compiz All Messed Up."
date: 2013-02-20
forum: Desktop Environments
---

### Post by cbanakis on 2013-02-20
If someone could please help me figure this out.

I was running a customized 12.04.

(No Unity)
(Compiz Cube)
(Cairo Dock)

I upgraded to 12.10, and now things are pretty messed up.

I cannot enable compiz.
```
chris@chris-ET2410:~$ compiz
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Error: Screen 0 on display ":0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core
chris@chris-ET2410:~$ compiz -- replace
compiz (core) - Warn: Unknown option '--'

compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Error: Screen 0 on display ":0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core

```I tried this, and terminal just seemed to hang.
```
$ compiz --replace ccp & emerald --replace &
[1] 3192
[2] 3193
chris@chris-ET2410:~$ compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
emerald: command not found
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
```

Also, I un-installed Cairo-Dock, so I could try to get back to Unity.
(Figured I could start from scratch)

But despite the fact that I removed cairo, its still there?

Not sure what to make of any of this.

Any help would be greatly appreciated.

Thanks

---

### Post by grahammechanical on 2013-02-21
Upgrades are not designed to deal with heavily modified desktop environments. There are every so many ways in which we can modify the User Interface that it is impossible for the developers to script an upgrade process that will take into account all possible modifications.


It may be easier to re-install.

Regards.

---

### Post by cbanakis on 2013-02-27
Yeah, I assumed the cause was all the mod's I did.

I was hoping there would be an easy way to fix, but I ended up doing a backup, and clean install.

All is well now.

Thanks for your post.

> **grahammechanical said:**
> Upgrades are not designed to deal with heavily modified desktop environments. There are every so many ways in which we can modify the User Interface that it is impossible for the developers to script an upgrade process that will take into account all possible modifications.


It may be easier to re-install.

Regards.

---

