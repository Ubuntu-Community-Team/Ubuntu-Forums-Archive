---
title: "Unable to open preferences in elevated file manager"
date: 2017-11-07
forum: Desktop Environments
---

### Post by shag00 on 2017-11-07
Ubuntu 17.10 - opening preferences for normal user file manager is simple, just click "Files" in the top bar and select preferences from the drop down menu however in elevated (gksudo) file manager "Files" just highlights with with no drop down menu. Am I missing something or is this a bug?

---

### Post by ajgreeny on 2017-11-07
This may be another symptom of the wayland root GUI application access problems shown in these two threads:-
[https://ubuntuforums.org/showthread.php?t=2366995](https://ubuntuforums.org/showthread.php?t=2366995)
[https://askubuntu.com/questions/968675/missing-xauthority-file-in-wayland-but-not-in-xorg](https://askubuntu.com/questions/968675/missing-xauthority-file-in-wayland-but-not-in-xorg)

You should be able to either login to an xorg session from the login screen, or if you prefer to use wayland sessions run the command shown in those threads ```
xhost +si:localuser:root
``` by adding it as a command in the startup applications you have setup.

---

### Post by shag00 on 2017-11-07
I suspected as much but that should not affect me as I log in to an Xorg session. I also think 
xhost +si:localuser:root does not work anymore

---

### Post by jbicha on 2017-11-11
Please do not try to run your file manager with gksu, sudo, etc. in Ubuntu 17.10. Instead, use the *gvfs admin backend* by using the prefix **admin://**

For instance, if you want to view the directory where default grub bootloader settings are kept, press Ctrl+L to edit the location. Enter
```

admin:///etc/default/

```

This works in many apps. For instance, to edit your grub settings with gedit, open this file
```

admin:///etc/default/grub

```

The gvfs admin backend is available starting in Ubuntu 17.04.

---

### Post by shag00 on 2017-11-12
I suppose it's a silly question to ask why the gvfs backend was not included as part of the core system installation...

---

### Post by jbicha on 2017-11-13
The gvfs admin backends is included in Ubuntu 17.04 and newer. It just has some UI problems in that it's not very discoverable yet. (But to be fair, 'gksu nautilus' isn't discoverable either.)

The admin backend is a new feature in gvfs, one of the key system libraries for the Ubuntu desktop. That's why it isn't available in 16.04 LTS but it is available in newer Ubuntu versions without needing to install anything extra.

---

