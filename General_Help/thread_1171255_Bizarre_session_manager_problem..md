---
title: "Bizarre session manager problem."
date: 2009-05-27
forum: General Help
---

### Post by perrti-y02 on 2009-05-27
Hello,
I am having a little bit of a problem with logging onto my machine with XFCE4. What happens is I type in my name and password (XFCE4 is set to the standard session) and then GNOME and XFCE4 open one on top of the other. The panel is always xfce but the desktop is either gnome or xfce. I can tell the difference both as far as wall paper is concerned and the fact that i don't get the menu for programs when I right click on the gnome desktop.

Anyone know what is happening? It is fairly annoying.

---

### Post by Brandon Williams on 2009-05-27
What is the content of your ~/.dmrc file? It should look something like this:
```

[Desktop]
Session=xfce
```
The value after 'Session=' should correspond to a *.desktop file in /usr/share/xsessions/. In my case, the file is /usr/share/xsessions/xfce.desktop. In releases prior to Jaunty, it was xfce4 instead of just xfce. After the upgrade to Jaunty, I think that I might have had to update my .dmrc file to represent the new session file name, although deleting .dmrc and logging in again with the correct session type selected probably would have been enough.

---

### Post by perrti-y02 on 2009-05-28
The only thing in that file is
> 


[Desktop]
session=xfce


there is nothing else.

The file in /usr/share/xsessions  is "xfce.desktop"

Should these match exactly?

---

### Post by perrti-y02 on 2009-05-28
It has now changed such that the xfce panel is visible but ONLY the gnome desktop will open. It doesn't open xfce desktop at all.

Tres annoying.

Any solutions?

---

### Post by Brandon Williams on 2009-05-29
Weird ... that all looks right to me ...

What does the Exec line in /usr/share/xsessions/xfce.desktop say? It should be 'Exec=startxfce4'.

If that's correct (I expect it will be), then logout from X, Ctrl+Alt+F1 to get to a console, login, and run these commands:
```
$ sudo invoke-rc.d gdm stop
$ startxfce4
```
Does xfce run correctly when you do this? If not, then there's a problem in xfce initialization. If it does run correctly, then there's a problem somewhere in the gdm session initialization.

After running that test, exit the graphical session to get back to a console command prompt and run 'sudo invoke-rc.d gdm start' to get your graphical login back.

If the above test worked to run xfce, then as a short-term workaround until you find the 'real' source of the problem, you might try creating a ~/.xsession file. Give it the following content:
```
#!/bin/sh
exec startxfce4
```
'chmod u+x ~/.xsession' to make the script executable and specify the 'Run Xclient script' session when you log in via gdm.

---

### Post by RogergR on 2009-05-29
Go to synaptic and reinstall xfce. No terminal, no keyboard, just klik...

---

### Post by perrti-y02 on 2009-05-30
The Exec line in the file mentioned is correct, as you expected, the commands suggested did not work.

On to of that completely uninstalling XFCE4 didn't work either so I am even more vexed.

Any more suggestions? Thanks for your help so far.

---

### Post by Brandon Williams on 2009-05-30
Did you purge the config files when you removed XFCE? If not, then try the remove and reinstall again, but purge the config files this time. I don't think this will solve the problem, but it's worth a try.

Next, look for a file called ~/.config/xfce4/xinitrc and, rename it, log out, and log back in. Other files to try this with are ~/.xsession, ~/.xinitrc, ~/.xsessionrc, and ~/.xprofile, each of which may come into play during session initialization, though the first one is the most likely if startxfce4 isn't working from a console login without gdm.

---

### Post by perrti-y02 on 2009-05-30
To purge the config files do I need to "COmpletely remove (including configuration files)" in Synaptic?

What packages do I actually need to remove? before i just removed anything with xfce4 in the name because that was fairly simple (removing one leads to removing anything that depends on it) but to remove config files as well is a bit of a pain.

---

### Post by perrti-y02 on 2009-05-30
Not a single one of those files exist in my setup. the closest thing is .xsession-errors which looks as follows


```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
/etc/xdg/xfce4/xinitrc: 59: source: not found
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7

(xfce4-panel:5651): xfce4-panel-WARNING **: xfce4-panel is not running
evolution-alarm-notify-Message: Setting timeout for 38263 1243724400 1243686137
evolution-alarm-notify-Message:  Sun May 31 00:00:00 2009

evolution-alarm-notify-Message:  Sat May 30 13:22:17 2009

Initializing nautilus-dropbox 0.6.1

** (nautilus:5657): WARNING **: Unable to add monitor: Not supported
** (update-notifier:5659): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)
** (update-notifier:5659): DEBUG: crashreport_check


** (xfce4-session:5612): WARNING **: Unable to launch "xfce4-volstatus-icon" (specified by autostart/xfce4-volstatus-icon.desktop): Failed to execute child process "xfce4-volstatus-icon" (No such file or directory)

** (xfce4-session:5612): WARNING **: Unable to launch ""/opt/BBC iPlayer Desktop/bin/BBC iPlayer Desktop"" (specified by autostart/BBC iPlayer Desktop.desktop): Failed to execute child process "/opt/BBC" (No such file or directory)
Initializing trackerd...
Tracker-Message: Checking XDG_DATA_HOME is writable and exists
Tracker-Message:   XDG_DATA_HOME is '(null)'
Tracker-Message:   XDG_DATA_HOME set to '/home/tim/.local/share'
Tracker-Message:   Path is OK
Tracker-Message: Setting IO priority
Tracker-Message: Setting up monitor for changes to config file:'/home/tim/.config/tracker/tracker.cfg'
Tracker-Message: Loading defaults into GKeyFile...
Tracker-Message: Legacy config option 'IndexEvolutionEmails' found
Tracker-Message:   This option has been replaced by 'DisabledModules'
Tracker-Message:   Option 'DisabledModules' removed 'evolution'
Tracker-Message: Legacy config option 'IndexThunderbirdEmails' found
Tracker-Message:   This option is no longer supported and has no effect
Tracker-Message: Legacy config option 'SkipMountPoints' found
Tracker-Message:   Option 'IndexMountedDirectories' set to true
Tracker-Message: Setting up stopword list for language code:'en'
Tracker-Message: Setting up stemmer for language code:'en'
Tracker-Message: Checking directory exists:'/home/tim/.local/share/tracker/data'
Tracker-Message: Checking directory exists:'/home/tim/.cache/tracker'
Tracker-Message: Registering DBus service...
  Name:'org.freedesktop.Tracker'
Starting log:
  File:'/home/tim/.local/share/tracker/trackerd.log'
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
Starting Dropbox...
** (update-notifier:5752): WARNING **: already running?

14
** (nm-applet:5740): DEBUG: applet_common_device_state_changed
** (nm-applet:5740): DEBUG: applet_common_device_state_changed
Done!
** (nm-applet:5740): DEBUG: applet_common_device_state_changed
** (nm-applet:5740): DEBUG: applet_common_device_state_changed
** (update-notifier:5659): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
Reusing existing ksycoca
DCOP Cleaning up dead connections.
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
get fences failed: -1
param: 6, val: 0
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".
Xlib:  extension "XFree86-Misc" missing on display ":0.0".

** (xfwm4:5646): WARNING **: Last user time set back to 7833363 (was 7920657)

** (xfwm4:5646): WARNING **: Last user time set back to 8364450 (was 8367184)

(firefox:9551): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(Thunar:5647): Gtk-WARNING **: Error loading theme icon 'Terminal' for stock: Icon 'Terminal' not present in theme
ERROR: meta.c (179): wmf_header_read: this isn't a wmf file
/usr/lib/thunar/thunar-vfs-pixbuf-thumbnailer-1: Error scanning WMF file.
```

This says that the X server is already running elsewhere. Could this be the problem?

---

### Post by Brandon Williams on 2009-05-30
You've got the correct option in Synaptic for purging config files, but if it were me, I wouldn't use synaptic, because you probably don't want to remove XFCE while you're using it. Instead, I would go to a console login, as described in one of the previous posts, and use aptitude, which is a console package manager with all the same functionality as synaptic. Search for the xfce4 meta-package and purge it and all it's dependencies. Read up on how to navigate, search, etc. in the aptitude man page.

Before doing all of that, though, I went back and read through the previous posts and it occurred to me that this might be more simple than I originally thought. It may be that what you've got is juat a standard xfce desktop with nautilus running, which would make it seem like the desktop is a gnome desktop. Open the 'Session and Startup' configurator (Applications->Settings->Session and Startup) and click on the Session tab. Is nautilus listed as a Program? If so, click on it to highlight the bar, then click the 'Quit Program' button, and then click 'Terminate nautilus'. Does the desktop go back to being the xfce desktop (right-click brings up applications menu)? If so, check 'Automatically save session on logout' on the General tab, and then look through the 'Application Autostart' list to make sure there is no item to start nautilus (delete it if there is). Finally, close 'Session and Startup', log out, and log back in.

Whether or not this solved the problem, go back to 'Session and Startup' and uncheck 'Automatically save session on logout' (unless you want that behavior), and then post back to let us know whether or not that solved the problem.

---

### Post by perrti-y02 on 2009-06-01
Stopping nautilus doens't return the desktop to xfce but it does stop it from doing ANYTHING. This to me says that the gnome element is gone but nothing is replacing it.

Any idea how to rectify that?

I will try removing it properly and rebooting to see if that gives me XFCE back.

---

### Post by perrti-y02 on 2009-06-01
I have rebooted and I now have no desktop at all. Everything else is working fine (panel, individual windows) just no desktop.

What would I need to add to the startup things to get the xfce4 desktop back?

---

### Post by Brandon Williams on 2009-06-01
Is xfdesktop running? That is what provides wallpaper, right-click menu, etc.

---

### Post by perrti-y02 on 2009-06-02
xfdesktop isn't running.

I started it from the terminal and everything is now spiffing once more.

If ti fails at a reboot I shall post here again, but I doubt that will happen.

Thank you very much for your help, it has been very informative and solved my problem.

---

### Post by perrti-y02 on 2009-06-02
How do I mark this thread as solved and how do I "Thank" you?

---

