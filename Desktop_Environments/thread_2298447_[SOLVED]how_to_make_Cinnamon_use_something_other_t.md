---
title: "[SOLVED]how to make Cinnamon use something other than nautilus for removable media?"
date: 2015-10-11
forum: Desktop Environments
---

### Post by jamesjones01 on 2015-10-11
I am running Ubuntu 15.10 beta 2 and using Cinnamon.

When I power up a USB docking station with a hard drive in place, it starts nautilus and points it at the drive so I can see and manipulate files there, which is fine... but nautilus changes the desktop, most notably the wallpaper.

I have looked around on the web and, following the advice I saw, changed the Exec line in /etc/xdg/autostart/nautilus-autostart.desktop to

[FONT=courier new]Exec=nautilus -n --no-desktop[/FONT]

and run the commands

```
[FONT=courier new]gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false[/FONT]
[FONT=courier new]gconftool-2 -s -t bool /desktop/gnome/background/draw_background false[/FONT]
```

to no effect.

So now I am looking for a way to have Cinnamon use some other application when a removable device is inserted, but Preferred Applications>Removable Media, while it gives one a choice of what to do on insertion/connection of DVDs, CDs, cameras, music players, and software media, doesn't show an option for what to do when one connects a plain disk drive/USB flash drive.

Any pointer to how to get Cinnamon to do something other than run nautilus when removable devices are connected would be greatly appreciated. (For that matter, if there is anywhere that the GNOME developers have stated a justification for having a file manager change the desktop background when invoked, I would dearly love to see it.)

UPDATE:  [http://www.fandigital.com/2013/01/set-nemo-default-file-manager-ubuntu.html](http://www.fandigital.com/2013/01/set-nemo-default-file-manager-ubuntu.html) tells how to avoid nautilus by having nemo as the default file manager:

```
[COLOR=#660000]xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search[/COLOR]
```

I'd still love to find out what in the name of the Unix philosophy persuaded the people working on nautilus that a file manager should fiddle with the desktop wallpaper.

---

