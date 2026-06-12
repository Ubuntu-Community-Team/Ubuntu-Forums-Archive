---
title: "iccons at xfce desktop dissappear"
date: 2018-11-13
forum: Desktop Environments
---

### Post by fik236 on 2018-11-13
Hello,
I have problem that iccons at my xfce desktop dissappear.
I have Xubuntu 18.04 (xfce 4.12).

And suddenly i have not at desktop any iccon - no trash, no iccon of file system, no iccon of home folder, no iccon of any lunchers and no iccon of any files 
(and in desktop setting are all these types allowed).
Sooner I have it, but now nothing. I do not know what produce it (mabye some update).

I have created some testing user - and this user these iccons has at their desktop.

Please can you anybody advice me what should I check or correct to reapir it.

Please if somebody give me some advice, write detailed procedure how to do it - I am fairly new in Linux.

thanks for any advice

---

### Post by ajgreeny on 2018-11-13
Do you usually show just those system icons or do you also use launcher icons for applications as many users do?

Please show us the output of ```
ls -l Desktop
``` to check ownership of the Desktop folder and the ```
ls -la
``` to see if everything expected is still in your /home.

Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. 
See my signature below for a **How-to**

---

### Post by fik236 on 2018-11-13
Because I have czech localization of system, I have desktop in folder ~/Plocha/

and sooner was everithing visible as iccons :sad:

I have also in system folder ~/Desktop/ (which was empty) - but when I  have dicovered, that my iccons have dissappered, I have created there  testint text file - but it has also no icocn at desktop

so here is output of ls:


```
fik236u@notas-ubuntu:~/Plocha$ ls -la
celkem 44
drwxr-xr-x  2 fik236u fik236u 4096 lis 13 10:41  .
drwxr-xr-x 60 fik236u fik236u 4096 lis 13 06:47  ..
-rwxr-xr-x  1 fik236u fik236u  334 &#269;ec 12 07:32 'Fallout 4.desktop'
-rw-rw-r--  1 fik236u fik236u  660 &#269;ec 11 19:56 'Fallout 4.lnk'
-rwxrwxr-x  1 fik236u fik236u  263 kv&#283; 22 20:26  Tull.desktop
-rw-rw-r--  1 fik236u fik236u  276 lis 13 08:15  veci_na_privezeni.txt
-rwxr-xr-x  1 fik236u fik236u  369 &#269;en 24 14:50 'World of Tanks.desktop'
-rwxrwxr-x  1 fik236u fik236u  233 kv&#283; 22 20:28  Zapas.desktop
-rw-rw-r--  1 fik236u fik236u  727 lis 13 10:41  zmizle_ikonky.txt
-rwxrwxr-x  1 fik236u fik236u  271 kv&#283; 22 20:29  ZobrazKategorii.desktop
-rwxrwxr-x  1 fik236u fik236u  241 kv&#283; 22 20:22  ZpracujPrihlasky.desktop
fik236u@notas-ubuntu:~/Plocha$ cd ..
fik236u@notas-ubuntu:~$ cd ./Desktop/
fik236u@notas-ubuntu:~/Desktop$ ls -la
celkem 12
drwxr-xr-x  2 fik236u fik236u 4096 lis 12 15:41 .
drwxr-xr-x 60 fik236u fik236u 4096 lis 13 06:47 ..
-rw-rw-r--  1 fik236u fik236u   15 lis 12 15:41 pokus.txt
```

thanks for any advice

---

### Post by ajgreeny on 2018-11-13
I'm sorry but I am confused.

It looks as if within the filesystem you have the standard user setup with /home/fik236u as the normal home folder, and within that you have another folder named /Plocha where you are having the icon problem with the "Desktop" folder?

If that is correct I think the problem relates to that Plocha desktop not being a Desktop folder of a normal user, and therefore it does not follow the expected behaviour of a Desktop folder in a user's home.

Why not create a new user named plocha? You would then have both the **/home/fik236u** and **/home/plocha** folders where they would normally be and both Desktop folders should behave as you want.

---

### Post by him610 on 2018-11-14
Navigate to Settings > Desktop > Tab Icons 
From there, you should be able to choose Icon types, Default Icons, size, and other attributes.

---

### Post by again? on 2018-11-14
You appear to have moved all your desktop launchers to **/home/fik236u/Plocha**
Should be in **/home/fik236u/Desktop**
"~" = /home/fik236u 

Why your ~/Desktop/pokus.txt test file is not showing, I do not know.
Does this command output "2"? (show file/launcher icons)
```
xfconf-query -c xfce4-desktop -p /desktop-icons/style
```

Do you have the xfce right click menu on the desktop?

---

### Post by fik236 on 2018-11-15
Hi Guys,
thanks for your answers...

I did not moved any file from ~/Desktop/ to ~/Plocha/

it was probably done with instalator when I have choose Czech language ... And after instalation everithing works fine.
Folder ~/Desktop/ was after instalation present too, but it was always empty

I can find in file ~/.config/user-dirs

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Plocha"
XDG_DOWNLOAD_DIR="$HOME/Stažené"
XDG_TEMPLATES_DIR="$HOME/Šablony"
XDG_PUBLICSHARE_DIR="$HOME/Ve&#345;ejné"
XDG_DOCUMENTS_DIR="$HOME/Dokumenty"
XDG_MUSIC_DIR="$HOME/Hudba"
XDG_PICTURES_DIR="$HOME/Obrázky"
XDG_VIDEOS_DIR="$HOME/Videa"
```

so it looks that folders are setted ok

I have also tryied change in this file row XDG_DESKTOP_DIR="$HOME/Plocha" to XDG_DESKTOP_DIR="$HOME/Desktop"
And I have hoped that icon of pokus.txt will be shown, but still nothing (so i have changed it back)

@guber2
as you can see (in attached printscreen) mentonied command answers 2, after right click does nothing happend
in printscreen is also visible, that I have in setting choosed option show "file iccons and launchers"



I have found file ~/.xsession-errors - but I do not anderstant them. 

```
dbus-update-activation-environment: setting DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
dbus-update-activation-environment: setting DISPLAY=:0
dbus-update-activation-environment: setting XAUTHORITY=/home/fik236u/.Xauthority
dbus-update-activation-environment: setting GTK_MODULES=gail:atk-bridge
dbus-update-activation-environment: setting QT_ACCESSIBILITY=1
dbus-update-activation-environment: setting LANG=cs_CZ.UTF-8
dbus-update-activation-environment: setting GDM_LANG=cs
dbus-update-activation-environment: setting DISPLAY=:0
dbus-update-activation-environment: setting GTK_OVERLAY_SCROLLING=0
dbus-update-activation-environment: setting JAVA_HOME=/usr/lib/jvm/java-8-oracle
dbus-update-activation-environment: setting J2SDKDIR=/usr/lib/jvm/java-8-oracle
dbus-update-activation-environment: setting MANDATORY_PATH=/usr/share/gconf/xubuntu.mandatory.path
dbus-update-activation-environment: setting XDG_GREETER_DATA_DIR=/var/lib/lightdm-data/fik236u
dbus-update-activation-environment: setting DERBY_HOME=/usr/lib/jvm/java-8-oracle/db
dbus-update-activation-environment: setting USER=fik236u
dbus-update-activation-environment: setting DESKTOP_SESSION=xubuntu
dbus-update-activation-environment: setting DEFAULTS_PATH=/usr/share/gconf/xubuntu.default.path
dbus-update-activation-environment: setting QT_QPA_PLATFORMTHEME=gtk2
dbus-update-activation-environment: setting PWD=/home/fik236u
dbus-update-activation-environment: setting HOME=/home/fik236u
dbus-update-activation-environment: setting J2REDIR=/usr/lib/jvm/java-8-oracle/jre
dbus-update-activation-environment: setting QT_ACCESSIBILITY=1
dbus-update-activation-environment: setting XDG_SESSION_TYPE=x11
dbus-update-activation-environment: setting XDG_DATA_DIRS=/usr/share/xubuntu:/usr/share/xfce4:/home/fik236u/.local/share/flatpak/exports/share:/var/lib/flatpak/exports/share:/usr/local/share:/usr/share:/var/lib/snapd/desktop
dbus-update-activation-environment: setting XDG_SESSION_DESKTOP=xubuntu
dbus-update-activation-environment: setting GTK_MODULES=gail:atk-bridge
dbus-update-activation-environment: setting CLUTTER_BACKEND=x11
dbus-update-activation-environment: setting SHELL=/bin/bash
dbus-update-activation-environment: setting XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
dbus-update-activation-environment: setting IM_CONFIG_PHASE=1
dbus-update-activation-environment: setting GPG_AGENT_INFO=/run/user/1000/gnupg/S.gpg-agent:0:1
dbus-update-activation-environment: setting SHLVL=1
dbus-update-activation-environment: setting LANGUAGE=cs
dbus-update-activation-environment: setting GDMSESSION=xubuntu
dbus-update-activation-environment: setting LOGNAME=fik236u
dbus-update-activation-environment: setting DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
dbus-update-activation-environment: setting XDG_RUNTIME_DIR=/run/user/1000
dbus-update-activation-environment: setting XAUTHORITY=/home/fik236u/.Xauthority
dbus-update-activation-environment: setting XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0
dbus-update-activation-environment: setting XDG_CONFIG_DIRS=/etc/xdg/xdg-xubuntu:/etc/xdg
dbus-update-activation-environment: setting PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/usr/lib/jvm/java-8-oracle/bin:/usr/lib/jvm/java-8-oracle/db/bin:/usr/lib/jvm/java-8-oracle/jre/bin
dbus-update-activation-environment: setting _=/usr/bin/dbus-update-activation-environment

** (wrapper-2.0:3108): WARNING **: 06:25:47.388: No outputs have backlight property

** (wrapper-2.0:3109): WARNING **: 06:25:47.803: Binding 'XF86AudioPlay' failed!

(wrapper-2.0:3109): pulseaudio-plugin-WARNING **: 06:25:47.803: Could not have grabbed multimedia control keys.

(wrapper-2.0:3106): GLib-GIO-CRITICAL **: 06:25:47.861: g_file_new_for_path: assertion 'path != NULL' failed

(wrapper-2.0:3106): GLib-GIO-CRITICAL **: 06:25:47.861: g_file_monitor_file: assertion 'G_IS_FILE (file)' failed

(wrapper-2.0:3106): GLib-GObject-WARNING **: 06:25:47.861: invalid (NULL) pointer instance

(wrapper-2.0:3106): GLib-GObject-CRITICAL **: 06:25:47.861: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(wrapper-2.0:3106): Gtk-WARNING **: 06:25:47.861: Attempting to add a widget with type GtkToggleButton to a container of type XfcePanelPlugin, but the widget is already inside a container of type XfcePanelPlugin, please remove the widget from its existing container first.

(wrapper-2.0:3106): Gtk-WARNING **: 06:25:48.270: Negative content width -3 (allocation 1, extents 2x2) while allocating gadget (node button, owner GtkToggleButton)

(wrapper-2.0:3108): Gtk-WARNING **: 06:25:48.668: Negative content width -3 (allocation 1, extents 2x2) while allocating gadget (node button, owner PowerManagerButton)

(wrapper-2.0:3122): Gtk-WARNING **: 06:25:49.676: Negative content width -1 (allocation 1, extents 1x1) while allocating gadget (node button, owner GtkButton)

(xfce4-session:2948): GLib-WARNING **: 06:25:52.119: GChildWatchSource: Exit status of a child process was requested but ECHILD was received by waitpid(). See the documentation of g_child_watch_source_new() for possible causes.

(polkit-gnome-authentication-agent-1:3190): GLib-CRITICAL **: 06:25:55.108: g_variant_new_string: assertion 'string != NULL' failed

(polkit-gnome-authentication-agent-1:3190): polkit-gnome-1-WARNING **: 06:25:55.109: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(wrapper-2.0:3107): Gtk-WARNING **: 06:25:56.477: Theme parsing error: <data>:1:46: The style property GtkWidget:focus-padding is deprecated and shouldn't be used anymore. It will be removed in a future version

(wrapper-2.0:3107): Gtk-WARNING **: 06:25:56.478: Theme parsing error: <data>:1:78: The style property GtkWidget:focus-line-width is deprecated and shouldn't be used anymore. It will be removed in a future version

(wrapper-2.0:3107): Gtk-WARNING **: 06:25:56.478: Theme parsing error: <data>:1:108: The style property GtkButton:default-border is deprecated and shouldn't be used anymore. It will be removed in a future version

(wrapper-2.0:3107): Gtk-WARNING **: 06:25:56.478: Theme parsing error: <data>:1:136: The style property GtkButton:inner-border is deprecated and shouldn't be used anymore. It will be removed in a future version
cannot read expected data from eventfd: Interrupted system call

(wrapper-2.0:3085): Gtk-WARNING **: 06:26:02.239: Negative content width -3 (allocation 1, extents 2x2) while allocating gadget (node button, owner GtkToggleButton)
support process for mount namespace capture exited abnormally

(nm-applet:3266): Gtk-WARNING **: 06:26:03.239: Can't set a parent on widget which has a parent

(nm-applet:3266): Gdk-CRITICAL **: 06:26:03.368: gdk_window_thaw_toplevel_updates: assertion 'window->update_and_descendants_freeze_count > 0' failed

(wrapper-2.0:3109): Gtk-WARNING **: 06:26:04.132: Negative content width -3 (allocation 1, extents 2x2) while allocating gadget (node button, owner PulseaudioButton)

(nm-applet:3266): Gtk-CRITICAL **: 06:26:04.146: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed

(nm-applet:3266): Gtk-CRITICAL **: 06:26:04.146: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed

(nm-applet:3266): Gtk-WARNING **: 06:26:04.149: Can't set a parent on widget which has a parent
ERROR mpg123.cc:348 [play]: mpg123 error in file:///mnt/data/mp3/mp3/Steve%20Vai%20Discography/Passion%20And%20Warfare%20%281990%29/06%20-%20Ballerina%2012_24.mp3: No error... (code 0)

(thunderbird:3167): Gtk-WARNING **: 06:26:13.488: Theme parsing error: <data>:1:34: Expected ')' in color definition

(thunderbird:3167): Gtk-WARNING **: 06:26:13.513: Theme parsing error: <data>:1:77: Expected ')' in color definition
JavaScript error: jar:file:///usr/lib/thunderbird/omni.ja!/components/XULStore.js, line 65: Error: Can't find profile directory.

(firefox:3043): Gtk-WARNING **: 06:26:19.346: Theme parsing error: <data>:1:34: Expected ')' in color definition

(firefox:3043): Gtk-WARNING **: 06:26:19.346: Theme parsing error: <data>:1:77: Expected ')' in color definition

(firefox:3145): Gtk-WARNING **: 06:26:20.736: Theme parsing error: <data>:1:34: Expected ')' in color definition

(firefox:3145): Gtk-WARNING **: 06:26:20.736: Theme parsing error: <data>:1:77: Expected ')' in color definition

(thunderbird:3042): Gtk-WARNING **: 06:26:22.150: Theme parsing error: <data>:1:34: Expected ')' in color definition

(thunderbird:3042): Gtk-WARNING **: 06:26:22.150: Theme parsing error: <data>:1:77: Expected ')' in color definition
Exiting because another libpurple client is already running.
JavaScript error: chrome://gdata-provider/content/gdata-migration.js, line 5: NS_ERROR_NOT_AVAILABLE: Component returned failure code: 0x80040111 (NS_ERROR_NOT_AVAILABLE) [nsIXPCComponents_Utils.import]
Chyba: &#268;asový limit vypršel

(tracker-miner-fs:3187): Tracker-CRITICAL **: 06:27:18.618:   (Sparql buffer) Error in task 0 (file:///home/fik236u/GoogleDisk) of the array-update: UNIQUE constraint failed: nie:DataObject.nie:url

(tracker-miner-fs:3187): Tracker-CRITICAL **: 06:27:18.618: Could not execute sparql: UNIQUE constraint failed: nie:DataObject.nie:url
JavaScript error: resource://messagingmenu/modules/MessagingMenuModule.jsm, line 795: ReferenceError: indicator is not defined

(nm-applet:3266): Gtk-CRITICAL **: 06:30:17.100: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed

(nm-applet:3266): Gtk-CRITICAL **: 06:30:17.100: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed

(nm-applet:3266): Gtk-WARNING **: 06:30:17.107: Can't set a parent on widget which has a parent

(nm-applet:3266): Gtk-CRITICAL **: 06:30:17.111: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed

(nm-applet:3266): Gtk-CRITICAL **: 06:30:17.111: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed

(nm-applet:3266): Gtk-WARNING **: 06:30:17.113: Can't set a parent on widget which has a parent

(blueman-applet:3224): Gdk-CRITICAL **: 06:40:31.471: gdk_window_thaw_toplevel_updates: assertion 'window->update_and_descendants_freeze_count > 0' failed
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

(wrapper-2.0:3085): Gdk-CRITICAL **: 06:42:00.841: Window 0x557410560010 has not been made visible in GdkSeatGrabPrepareFunc
JavaScript error: resource:///modules/activity/autosync.js, line 206: uncaught exception: 2147746065
JavaScript error: resource:///modules/activity/autosync.js, line 206: uncaught exception: 2147746065

(wrapper-2.0:3085): Gdk-CRITICAL **: 07:23:35.170: Window 0x557410560010 has not been made visible in GdkSeatGrabPrepareFunc

(wrapper-2.0:3085): Gdk-CRITICAL **: 07:24:39.372: Window 0x557410560010 has not been made visible in GdkSeatGrabPrepareFunc

(mousepad:5167): Gtk-WARNING **: 07:24:41.710: Theme parsing error: <data>:2:29: The style property GtkButton:default-border is deprecated and shouldn't be used anymore. It will be removed in a future version

(mousepad:5167): Gtk-WARNING **: 07:24:41.710: Theme parsing error: <data>:3:37: The style property GtkButton:default-outside-border is deprecated and shouldn't be used anymore. It will be removed in a future version

(mousepad:5167): Gtk-WARNING **: 07:24:41.710: Theme parsing error: <data>:4:27: The style property GtkButton:inner-border is deprecated and shouldn't be used anymore. It will be removed in a future version

(mousepad:5167): Gtk-WARNING **: 07:24:41.710: Theme parsing error: <data>:5:31: The style property GtkWidget:focus-line-width is deprecated and shouldn't be used anymore. It will be removed in a future version

(mousepad:5167): Gtk-WARNING **: 07:24:41.710: Theme parsing error: <data>:6:28: The style property GtkWidget:focus-padding is deprecated and shouldn't be used anymore. It will be removed in a future version

(doublecmd:5148): GLib-GObject-WARNING **: 07:37:35.474: ../../../../gobject/gsignal.c:1207: no emission of signal "button-release-event" to stop for instance '0x38bb370'
```

Thanks for any answer

---

### Post by again? on 2018-11-15
Yeah sorry wasn't paying attention as Plocha is Desktop in Czech.
So, everything appears to be ok but the desktop icons don't show for you.
I created a test account and changed to czech laguage just for the user and it appeared to work.
[[img]https://cdn.scrot.moe/images/2018/11/15/Vyber_001.th.png[/img]](https://www.scrot.moe/image/a0NYm)

[[img]https://cdn.scrot.moe/images/2018/11/15/1_002.th.png[/img]](https://www.scrot.moe/image/a0TE6) 

Have you installed any other desktops or file managers?
Can you change the desktop wallpaper.
In xfce, xfdesktop draws the wallpaper and desktop icons.
Is xfdesktop running?
```
ps aux | grep [x]fdesktop
```
eg.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] ps aux | grep [x]fdesktop**
glen     13890  4.7  1.1 566836 47944 ?        Sl   05:25   0:00 xfdesktop
```

Try reloading...
```
xfdesktop --reload
```

---

### Post by fik236 on 2018-11-17
Hi,
desktop - you mean gnome or similar -> no I have only Xfce

I have except Thunar - Double commander - but i have not it installed immideateley before iccon dissapearing

So I have tryied command ps. And as you can see xfdesktop was not running. So I have it reload and iccons are now showing.
And I have restarted system and they are still showing - thanks a lot.

Please do you know were is some log file from xfdesktop placed? To check what happened?

Once more Thank you lot.

---

### Post by again? on 2018-11-17
Don't know where you would find a log file but if it's ok after a reboot should be fine now.
If you have the problem again, consider clearing any saved sessions.

---

### Post by cesardag on 2018-12-28
I'm here for the same reason. I can only make "Ctrl + F6" and then "Ctrl + F7" and there it is.
But I think it was the last update... or configuring the nvidia card. Not sure.
I've tried with all the recomendation above, but nothing make it work again.

---

### Post by cesardag on 2018-12-28
I also have noticed that the bar is "working". I've made one click top-left and two "key-down", and then "Ctrl+F6" and "Ctrl+F7" and the menu is there,  deployed.

---

### Post by cesardag on 2019-02-21
I've found a solution:

taken from [https://ubuntuforums.org/showthread.php?t=2390433](https://ubuntuforums.org/showthread.php?t=2390433)

[COLOR=#000000][/COLOR]"I did manage to get things sorted out regarding xorg with  CompositionPipeline enabled on boot by deleting the secondary display  position values in the displays.xml file for xfce in  /home/XXXXX/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml  (deleting that file also works)."


Yes, it works.

---

