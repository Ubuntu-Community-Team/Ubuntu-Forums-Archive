---
title: "Thunderbird starts up &amp; goes away in Gnome, sticks around in KDE"
date: 2007-08-10
forum: Desktop Environments
---

### Post by peterwr on 2007-08-10
When I start Thunderbird in Gnome, it fires up to the point at which it displays the opening screen - i.e. the message list etc without any message selected - then after about a second it just goes away. No error message, nothing. It disappears from the screen and its button disappears from the panel. 

If I start it up under KDE, everything works fine. 

Any ideas? 

TIA...

---

### Post by miggols99 on 2007-08-10
Could you post the output of "thunderbird" (without quotes) in the terminal? This may tell us some error messages you may be getting.

---

### Post by peterwr on 2007-08-14
OK, here we go. I tried typing thunderbird into a gnome terminal and as you can see, it wasn't recognised. I got the properties from the panel icon and it wanted mozilla-thunderbird, so I typed that instead. Here's the terminal session (xxx is substituted for my username, obviously):

```
xxx@xxx:~$ thunderbird
bash: thunderbird: command not found

xxx@xxx:~$ mozilla-thunderbird
GTK Accessibility Module initialized
/home/xxx/.themes/Clearlooks-NeXT/gtk-2.0/gtkrc:49: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/xxx/.themes/Clearlooks-NeXT/gtk-2.0/gtkrc:50: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/xxx/.themes/Clearlooks-NeXT/gtk-2.0/gtkrc:51: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 
(Gecko:6754): GLib-GObject-WARNING **: gsignal.c:1019: unable to lookup signal "activate" of unloaded type `MaiAtkObject'

(Gecko:6754): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `signal_id > 0' failed
Segmentation fault (core dumped)
xxx@xxx:~$ 

```

FWIW, I'm using Beryl, but it's set my window manager and decorator to metacity and GTK, respectively.

---

### Post by kellemes on 2007-08-14
First you can try to disable/uninstall all extensions and themes from tb and restart, because maybe one of those is giving crap.
Another thing to try is to delete your profile and create it again..
If there are emails to keep... create backup of profilefolder OR let the profilemanager NOT delete profilefolder.
```
thunderbird -profilemanager
```

---

### Post by misfitpierce on 2007-08-14
Could also try deleting the Thunderbird folder under your directory and reloading program or just straight installing it again and delete folders for fresh install. Automatix can pre-configure thrunderbird for ubuntu and when I ran it in gnome it ran fine from automatix.

---

### Post by kellemes on 2007-08-14
> **misfitpierce said:**
> Could also try deleting the Thunderbird folder under your directory and reloading program or just straight installing it again and delete folders for fresh install. Automatix can pre-configure thrunderbird for ubuntu and when I ran it in gnome it ran fine from automatix.

Automatix may work very well.. **or** kill your system all together.
Good luck.

---

