---
title: "GDM broken - login window never appears"
date: 2007-06-04
forum: Desktop Environments
---

### Post by Shampyon on 2007-06-04
If GDM is set as default, it doesn't load. Ubuntu boots to the point where the GDM login should load, but the spinning cursor appears and nothing else. I tried reinstalling GDM. Setup produced this:

```
Setting up gdm (2.18.1-0ubuntu1) ...
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not suppported and will be ignored.
grep: /etc/X11/default-display-manager: No such file or directory
Adding group 'gdm' (GID 113) ...
Done.
Warning: The home dir you specified already esists.
Adding new user 'gdm' (UID 108) ...
Adding new user 'gdm' (UID 108) with group 'gdm' ...
The home directory '/var/lib/gdm' already exists. Not copying from '/etc/skel'.
adducer: Warning: that home directory does not belong to the user you are currently creating.
 * Reloading GNOME Display Manager configuration...
 * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
```

I tried doing dpkg-reconfigure gdm before and after the reinstall and got the same error: 
```
sudo dpkg-reconfigure gdm
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

```

I'm stuck using KDM for login, but since I'm using GNOME I have no menu access to change the theme of KDM. I'm hoping for a fix to the GDM problem, but failing that some tips on how to enable access to the KDM theme options would be appreciated.

---

### Post by jdkchem on 2007-06-22
try sudo /etc/init.d/gdm restart after you sudo dpkg-reconfigure gdm

---

### Post by dafrak on 2007-06-27
1. Restore any working backup of xorg.conf (eg. copy /etc/X11/xorg.conf.20070620110816 to /etc/X11/xorg.conf)

2. Restart the machine (sometimes there could be errors in display without restart)

3. ```
sudo dpkg-reconfigure gdm
``` - should be no errors

4. Optionally ```
sudo dpkg-reconfigure xserver-xorg
```

Hope it helps

---

