---
title: "how to mount only, without opening file browser"
date: 2009-10-28
forum: Desktop Environments
---

### Post by barna on 2009-10-28
Hi,
when an usb extern drive was plugged in in kde3, an icon appeared on the desktop, and the menu available via right-click contained a 'Mount' entry. 
In kde4's device notifier I can only choose to open it in a file browser. However, most of the time I want to access my drives from the console only, I would like to mount it without opening a file browser. How can it be done?
Thanks

---

### Post by dj-toonz on 2009-10-28
I don't know about KDE but in gnome, in the file browser , edit, preferences,  Media, untick browse media when Inserted, then in a console it's cd /media/disk or something like that, there should be something the same in KDE, hope somebody can help you better

---

### Post by kyrontf on 2009-10-28
Hi barna,

I'm not using Kubuntu, but I do have a box with KDE on it and I think you can do this by configuring a custom device action. Under the 'Advanced' tab of your System Settings, there should be something called 'Device Actions'. You can add an action to mount your device there. I found the default conditions worked for my external drive, so I just gave the action a name and specified 'mount %d' as the command. %d expands to the device node of the drive.

%f, the mount point of the device seems to work too.

After configuring the action, the Device Notifier should say that there is more than one action available for the device.  When you click on it, it should give you a menu which includes your new action.

Hope this helps!

---

