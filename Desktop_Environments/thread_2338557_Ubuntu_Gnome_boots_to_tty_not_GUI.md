---
title: "Ubuntu Gnome boots to tty not GUI"
date: 2016-09-29
forum: Desktop Environments
---

### Post by Aeretic on 2016-09-29
When I boot the graphical login screen doesn't show up and I get a tty instead.
If I login in the tty and run _*startx*_everything works fine.
If I logout without restarting I still have the graphical login.
The last thing I did was trying to set auto login in Account Settings.

I'd like to either bring back the graphical login or simply auto login.
It's not a matter of life or death but I'd like to understand what's happening and learn something.

---

### Post by ajgreeny on 2016-09-29
It would appear that your display manager, gdm I think, is not autostarting at first cold boot for some reason.  Can I also check which version of Ubuntu-gnome you are using; as startx works I assume that it is probably 14.04 as I believe **startx** is no longer working in 16.04.

If Ubuntu-gnome has a GUI utility for setting up sessions see what the settings are for gdm display manager and change them if necessary.

Have a look in /etc/init/gdm.conf if it exists (it may not but I've never used Ubuntu-gnome so I am not sure).
/etc/init/gdm.conf should I think contain lines similar to 
```
start on ((filesystem
           and runlevel [!06]
           and started dbus
           and plymouth-ready)
          or runlevel PREVLEVEL=S)
```
which are the lines setting out the startup config of gdm, the first line of which means start when the filesystem does.  If that line is absent or is commented out with a # at the start, edit or add the line.

---

