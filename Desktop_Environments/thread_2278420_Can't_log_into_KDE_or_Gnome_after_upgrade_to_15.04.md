---
title: "Can't log into KDE or Gnome after upgrade to 15.04"
date: 2015-05-16
forum: Desktop Environments
---

### Post by spraff on 2015-05-16
Hi and thanks for reading.

I just upgraded Kubuntu to 15.04. When I get to the graphical login screen, after my password is accepted, I get the KDE splash screen with a loading progress bar, then it blacks out and dumps me back at the login screen again. I can log in if I select e.g. LXDE or Openbox as my DE but not KDE or Gnome.

I tried [this advice]("http://ubuntuforums.org/showthread.php?t=1885401"), to no avail:
[INDENT]    sudo apt-get install gdm (select sddm in the configuration dialog)
    sudo dpkg-reconfigure gdm (and select sddm again)
    sudo apt-get remove gdm[/INDENT]

Here is my [~/.xsession-errors]("http://pastebin.com/RuaddUgS") from a failed KDE launch. A possibly significant line is this:
[INDENT]Qt: Session management error: networkIdsList argument is NULL[/INDENT]
And here is the tail
[INDENT]kscreen.kded: Config KScreen::Config(0xa514e0) is ready
kscreen.kded: Applying config
kscreen.kded: Calculating config ID for KScreen::Config(0xa514e0)
kscreen.kded: 	Part of the Id:  "8081cf91009d8f3909800987c52a390b"
kscreen.kded: 	Config ID: "f94dcacbcbba492827e2007607e85a6a"
kscreen.kded: Applying ideal config
kscreen.kded: "DP1"  Disabled
kscreen.kded: "DP2"  Disabled
kscreen.kded: "DP3"  Disabled
kscreen.kded: "HDMI1"  Disabled
kscreen.kded: "HDMI2"  Disabled
kscreen.kded: "HDMI3"  Disabled
kscreen.kded: "VGA1"  Disabled
kscreen.kded: "VIRTUAL1"  Disabled
kscreen.kded: "DP-0"  Disabled
kscreen.kded: "DP-1"  Disabled
kscreen.kded: Connected outputs:  1
kscreen.kded: doApplyConfig()
QXcbConnection: Could not connect to display :0
QXcbConnection: Could not connect to display :0
kwin_x11: FATAL ERROR while trying to open display :0
QXcbConnection: Could not connect to display :0
kdeinit5: PID 8009 terminated.
kdeinit5: PID 8008 terminated.
kdeinit5: PID 8010 terminated.
QXcbConnection: Failed to get the primary output of the screen
The X11 connection broke (error 1). Did the X11 server die?
QXcbConnection: Failed to get the primary output of the screen
The X11 connection broke (error 1). Did the X11 server die?
QXcbConnection: Failed to get the primary output of the screen
The X11 connection broke (error 1). Did the X11 server die?
kdeinit5: Fatal IO error: client killed
kdeinit5: sending SIGHUP to children.
klauncher: Exiting on signal 1
kdeinit5: sending SIGTERM to children.
kdeinit5: Exit.
QXcbConnection: Failed to get the primary output of the screen
The X11 connection broke (error 1). Did the X11 server die?
Unexpected response from KInit (response = 0).
startkde: Could not start ksmserver. Check your installation.
Error: Can't open display: :0
Could not connect to D-Bus server: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-TcpGYkEBgY: Connection refused
startkde: Shutting down...
kdeinit5_wrapper: Warning: connect(/run/user/1000/kdeinit5__0) failed: : No such file or directory
Error: Can not contact kdeinit5!
startkde: Running shutdown scripts...
xprop:  unable to open display ':0'
xprop:  unable to open display ':0'
startkde: Done.
KCrash: Attempting to start /usr/bin/kdeinit5 from kdeinit
Warning: connect() failed: : No such file or directory
KCrash: Attempting to start /usr/bin/kdeinit5 directly[/INDENT]

Any idea what's going on? Thanks.

---

### Post by dino99 on 2015-05-16
glancing at journalctl might be help you better to identify the failure's reason(s)

have you made that dist-upgrade with a cleaned genuine version ? (no extra third party sources like ppa, ... and after purging the orphans)

---

### Post by v3.xx on 2015-05-16
I do not run kde, but did find this and I wonder if this beta package could be a solution.

[https://bugreports.qt.io/browse/QTBUG-31389](https://bugreports.qt.io/browse/QTBUG-31389)

Good luck

---

### Post by spraff on 2015-07-08
Hi, thanks for the tip but journalctl give me "No journal files were found." even though I am in systemd-journal group and even when I run sudo.

I'd appreciate a little more help here, thanks a lot.

---

