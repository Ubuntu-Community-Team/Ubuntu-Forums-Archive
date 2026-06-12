---
title: "Error removing kio-umountwrapper after uninstalling Kubuntu Desktop"
date: 2008-07-23
forum: Desktop Environments
---

### Post by carlolovearianne on 2008-07-23
I tried installing the kubuntu desktop package but after an hour or so I decided I didn't like it.The command sudo aptitude remove kubuntu-desktop didn't really do anything and I have to manually remove the KDE applications in Synaptic. I also managed to remove the Kubuntu boot splash but I can't seem to remove kio-unmountwrapper:

 ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 111kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 124866 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Please help.

---

### Post by tuxxy on 2008-07-23
Wise decison on removing it ;)

```
sudo apt-get remove kde*
```

---

### Post by carlolovearianne on 2008-07-23
> **tuxxy said:**
> Wise decison on removing it ;)

```
sudo apt-get remove kde*
```

I was just bored and decided to try it out but I was overwhelmed by the by the sea of options:) It just looked too busy and bloated for me. 


Now I can't even do a sudo apt-get upgrade without the kio-unmount error message breathing down my neck. 


Any ideas?

---

### Post by gjoellee on 2008-07-25
what I did, is write the following command > sudo apt-get install kio-umountwrapper and let it install, then just > sudo apt-get install <the next package that is broken or something> and it should be fine!

---

