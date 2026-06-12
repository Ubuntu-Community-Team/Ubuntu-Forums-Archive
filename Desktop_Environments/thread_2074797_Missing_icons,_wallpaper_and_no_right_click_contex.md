---
title: "Missing icons, wallpaper and no right click context menu, any ideas?"
date: 2012-10-22
forum: Desktop Environments
---

### Post by Roochiedoor on 2012-10-22
Hi everyone,
I've had the following issue for about 6 months starting with a version 11 pre 11.10 (not sure which one it was), just upgraded to 12.04 hoping the issue would go away but it didn't (upgrade not a clean install). I've looked everywhere and don't seem to be able to solve it. I'm not exactly a Linux guru, I just use it. I don't know how to fix it when it breaks. I was hoping someone may be able to point me in the right direction.

Problems (I believe they are all connected with desktop functions):
1)There are no icons on desktop
2) The right click context menu on the desktop does not work
3) I can't set the wallpaper. If I set it through Settings Manager > Desktop, it makes no difference it's always the same default one that comes with Xubuntu.

I've had this problem since some point in Xubuntu version 11. An update at some point may have caused the problem. It was not working in 11.10, I've just upgraded to 12.04 and there is no difference

I don't run Compositor, if I do the desktop is entirely gray, leaves window drag trails and I sometimes get focus order issues. e.g. The screen with focus will be behind the screen that does not have focus.

 - I have tried changing the tick box for save session on logout, it makes no difference

 - I use a startup script to set my system into dual screen /home/myusername/.screenlayout/screen.sh. The scripts screen settings were created by ARandr or Grandr or Xrandr (one of those)

My dual screen setup is a laptop with a large external display. The laptop screen goes on the left and the large screen on the right, but the system never remembers this arrangement which is why I use the script. Turning the script off and reverting to a single screen makes no difference to the desktop issue of wallpaper, right click and context menu

- I have played around with theme config files etc.. in the past before the problem occurred (I can't remember exactly what I did, but mostly changed colours etc... in the config files). Changing to a different theme that I haven't messed with doesn't solve the problem.

I was thinking that maybe the issue would be rectified with a newer version of xfwm? But have not been able to figure out how to change it without breaking anything and I was hoping 11.10 to 12.04 may have had a change (I still don't know if it has or not, I've forgotten what the command is to get the version number).

I run my main xfce panel at the top of the screen, and I sometimes run a 2nd panel at the bottom (kind of like OSX kicker style but I'm just using xfce panels, no cairo dock or anything). If I set the bottom panel to autohide it does not come back on mouse over actions (occasionally it does and I haven't worked out what the trigger is)

I don't know which log files to look out to try to find the problem (any tips for that? What sort of errors or warnings am I looking for?)

Any help would be greatly appreciated, otherwise I'll probably just wipe and it and start again soon.

---

### Post by Toz on 2012-10-22
Hello and welcome to the forums.

Points #1 and #2 seem to indicate that xfdesktop isn't running. You can check this by issuing the following command from a terminal window:
```
ps -ef | grep xfdesktop | grep -v grep
```
...(if xfdesktop is running, it should show up)

If its not running, try Alt+F2 and starting it up:
```
xfdesktop
```

It might also solve point #3. If not, do you have nautilus installed? If so, by default it will take control of the desktop.

If xfdesktop isn't starting after you logout and back in again, look at your ~/.xsession-errors file for an indication as to why. One clean way to fix this is to reset your saved sessions (this will erase all saved session information - which may be corrupted). To do so, delete the ~/.cache/sessions directory while not logged in to Xfce (at the login screen, press Ctrl+Alt+F1 and log in at the text console). Once logged in, issue the following commands:
```
cd ~/.cache
rm -rf sessions

```
Be careful with the "rm -rf" command that you type it in correctly.

---

### Post by Roochiedoor on 2012-10-22
Thankyou very much Toz! xfdesktop wasn't running
That solved the 3 problems and sped up the login time, once I removed the sessions like you mentioned.

Now I just have to track down the other errors in the .xsession-errors log. It looks like there are 3 issues here.
1) it's trying to load something Gnome orientated in polkit
2) A problem with an xfce4 indicator plugin
3) A problem with a gdk window not appearing.

Below is the log, I'll see if I can trouble shoot the rest but if you've got any ideas on those one? :)


> openConnection: connect: No such file or directory
cannot connect to brltty at :0
xrdb:  "Xft.hinting" on line 13 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7
xfce4-settings-helper: Another instance is already running. Leaving...
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-FG1Imq/pkcs11: No such file or directory

(polkit-gnome-authentication-agent-1:5409): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:5409): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(xfce4-indicator-plugin:5411): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:5411): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
** Message: applet now removed from the notification area

(xfce4-indicator-plugin:5411): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(xfce4-indicator-plugin:5411): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(Thunar:5346): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

---

### Post by Toz on 2012-10-22
I get those same errors on my system and AFAIK, I always have. I don't think they're important.

---

