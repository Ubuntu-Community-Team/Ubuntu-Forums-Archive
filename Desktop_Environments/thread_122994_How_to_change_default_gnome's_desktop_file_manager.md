---
title: "How to change default gnome's desktop file manager?"
date: 2006-01-28
forum: Desktop Environments
---

### Post by Trullo on 2006-01-28
hi all.. i was a kde user and now im under gnome.. until those days all is how i want but one thing is bothering to me..
i preffer konqueror instead of nautilus and the desktop file manager is nautilis by default.. so when i doubleclick on a desktop folder, it popups nautilus..
i was lookin all arround at 'gconf-editor' and gnome session startup files without result.. anybody knows how i can change it?

thanks for your time and sorru for my poor english.. gave great!

---

### Post by TheSource on 2006-01-29
Ya I wanted to use TuxCommander as my file manager. I put the binary in ".tuxcmd" in my home folder.

---

### Post by John Jason Jordan on 2006-01-29
[QUOTE=TheSource]Ya I wanted to use TuxCommander as my file manager. I put the binary in ".tuxcmd" in my home folder.[/QUOTE]
Did that make it the default file browser instead of Nautilus?

I even tried uninstalling Nautilus, but then all I get is an error message when I click on one of the entries in Places. Nautilus sux. I use Konqueror and I'd really like to figure out how to make it the default.

---

### Post by TheSource on 2006-01-29
[QUOTE=John Jason Jordan]Did that make it the default file browser instead of Nautilus?

I even tried uninstalling Nautilus, but then all I get is an error message when I click on one of the entries in Places. Nautilus sux. I use Konqueror and I'd really like to figure out how to make it the default.[/QUOTE]

Na thats just where I stuck the executable cause I think some of its log files or config files made the folder.

---

### Post by psychicdragon on 2006-01-29
To get rid of Nautilus on your desktop use the gconf-editor.
The key is /apps/nautilus/preferences/show_desktop
Then you might need to killall nautilus.

The Places menu only works with Nautilus. Maybe in the future it will work with other file managers that use Gtk Bookmarks (only Thunar that I know of).

---

### Post by Trullo on 2006-01-29
[QUOTE=psychicdragon]To get rid of Nautilus on your desktop use the gconf-editor.
The key is /apps/nautilus/preferences/show_desktop[/QUOTE]

Ok, nautilus is out of my desktop.. but this key only have true/false.. i cant "link" konqueror to work with..

---

### Post by TheSource on 2006-01-29
And how do you get rid of XFCE's file manager.?

---

### Post by Trullo on 2006-02-01
[QUOTE=TheSource]And how do you get rid of XFCE's file manager.?[/QUOTE]

sorry i dont know how about xfce.. but im still lookin how to put konqueror instead..:confused:

---

