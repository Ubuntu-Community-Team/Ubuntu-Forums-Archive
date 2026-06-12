---
title: "Want to access Synaptic with root password"
date: 2005-08-27
forum: Desktop Environments
---

### Post by JoeS on 2005-08-27
[QUOTE=codejunkie]if you want apps in the menu like synaptic for example to ask for the root password instead of your password, you have to manually edit it's .desktop file.
the reason it's not working is because the command in the System/Administration menu to launch synaptic is

```
gksudo /usr/sbin/synaptic
```

this will ask for your password, to make it ask for the root password you have to change it to

```
gksu /usr/sbin/synaptic
```

this will make it do what you want it to but it might take some time hunting down and editing those .desktop files hope this helps.

[/QUOTE]

I found 2 files:

    synaptic.desktop /etc/X11/sysconfig

    synaptic.desktop /usr/share/control-center-2.0/capplets


and edited them to:

    ```
Exec=gksu /usr/sbin/synaptic
```


I still cannot access synaptic with the root password. Any suggestions?

I also tried to open the synaptic and the update-manager through the terminal after switching to root and was denied. Why is this, If I'm in root shouldn't I be able to access?

Thanks for help.

---

