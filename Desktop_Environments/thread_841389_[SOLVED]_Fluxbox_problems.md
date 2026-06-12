---
title: "[SOLVED] Fluxbox problems"
date: 2008-06-26
forum: Desktop Environments
---

### Post by Inxsible on 2008-06-26
1) I have created a sub menu for Wallpapers like so ```
[submenu] (Wallpapers) {}
     [wallpapers] (/usr/share/fluxbox/backgrounds)
     [wallpapers] (~/Wallpapers)
[end]
``` I added this to my /etc/X11/fluxbox/fluxbox-menu because I wanted it to be permanent and not have fluxmenu screw it up. Anyway, whenever I reboot or exit Fluxbox and then login again, I lose that sub menu. Why is that? I have other menu entries added to the same file and they don't disappear on reboot !!

2) When I 'Exit' fluxbox, it takes me back to the CLI where I have to issue a ```
sudo shutdown -r now
``` to reboot. Is there a way I can add a logout, shutdown and restart (as in reboot) option to the fluxbox menu?

---

### Post by spupy on 2008-06-26
1) Do you have a ".flubox" folder in your home directory? Even if you change the setting in /etc, the ones in your /home might have a higher "priority" and get loaded instead.
Sidenote: I don't know why people put stuff in /usr and /etc. It is not a good practice, imho. User stuff should stay in the home folder, not fiddling with /usr, /etc or others. Do you have a good reason to change your settings in /etc?

2) I added this script to my fluxbox menu. It displays a gtk dialog where you can select to reboot, shutdown, hibernate, etc. It requires the "zenity" program. (I haven't tested it, but the hibernate and suspend options might not be working)

```
#!/bin/bash
action=`zenity --list --title='Powerbutton' --text='Choose action' --column=Action Hibernate Suspend Shutdown Restart`

if [ $action = "Hibernate" ]
	then
		zenity --question --title='Hibernate?' --text='Hibernate now?' && gksu 'echo -n "disk" > /sys/power/state'
fi
if [ $action = "Suspend" ]
	then
		zenity --question --title='Suspend?' --text='Suspend now?' && gksu "s2ram --force"
fi
if [ $action = "Shutdown" ]
	then
		zenity --question --title='Shutdown?' --text='Shutdown now?' && gksu "shutdown -h now"
fi
if [ $action = "Restart" ]
	then
		zenity --question --title='Restart?' --text='Restart now?' && gksu "shutdown -r now"
fi

```
If you don't want some of the options in the list, i can remove them.

---

### Post by Inxsible on 2008-06-26
my menu file in the folder includes the fluxbox-menu from /etc/X11/fluxbox.

So I don't think its a priority issue. On reboot, my menu file under etc gets re-written ??

because the Wallpaper entry that I put in, disappears completely.

---

### Post by spupy on 2008-06-26
> **Inxsible said:**
> my menu file in the folder includes the fluxbox-menu from /etc/X11/fluxbox.

So I don't think its a priority issue. On reboot, my menu file under etc gets re-written ??

because the Wallpaper entry that I put in, disappears completely.

Put some higher permissions on the file - remove writing for everyone? (don't worry, "sudo su" can always read/write)

---

### Post by RedSquirrel on 2008-06-26
I recommend you edit ~/.fluxbox/menu. The fluxbox-menu and menudefs.hook files under /etc can be overwritten by the system, for example, when you install new programs.

See the link in my signature for some ideas about Reboot/Shutdown from the menu.

---

