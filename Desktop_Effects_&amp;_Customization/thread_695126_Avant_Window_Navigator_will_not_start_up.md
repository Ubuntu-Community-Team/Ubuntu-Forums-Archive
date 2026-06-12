---
title: "Avant Window Navigator will not start up"
date: 2008-02-12
forum: Desktop Effects &amp; Customization
---

### Post by bvc310 on 2008-02-12
I just restarted my computer and avant didnt open at start up as it typically does. I went to my menubar and tried to start it from there to no avail. Then I tried to run it in terminal by ```
avant-window-navigator
```
When I did that i received the following errors
```
$ avant-window-navigator
Screen is composited.
LOADED : /usr/share/applications/gimp.desktop
LOADED : /usr/share/applications/inkscape.desktop
LOADED : /usr/share/applications/blender-windowed.desktop
LOADED : /usr/share/applications/xaralx.desktop
LOADED : /usr/share/applications/kde/kpovmodeler.desktop
LOADED : /usr/share/applications/frozen-bubble.desktop
LOADED : /usr/share/applications/sol.desktop
LOADED : /usr/share/applications/ooo-writer.desktop
LOADED : /usr/share/applications/jokosher.desktop
LOADED : /usr/share/applications/vlc.desktop
LOADED : /usr/share/applications/songbird.desktop
LOADED : /usr/share/applications/rhythmbox.desktop
LOADED : /usr/share/applications/pidgin.desktop
LOADED : /usr/share/applications/opera.desktop
LOADED : /usr/share/applications/firefox.desktop
LOADED : /usr/share/applications/kde/ktorrent.desktop
LOADED : /usr/share/applications/transmission.desktop
LOADED : /usr/share/applications/gnome-terminal.desktop
APPLET : /usr/local/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/showdesktop.desktop
APPLET : /usr/lib/awn/applets/trash.desktop

** (awn-applet-activation:7034): WARNING **: This desktop file does not exist /usr/lib/awn/applets/showdesktop.desktop

APPLET : /usr/lib/awn/applets/plugger.desktop

** (awn-applet-activation:7036): WARNING **: This desktop file does not exist /usr/lib/awn/applets/trash.desktop


** (awn-applet-activation:7038): WARNING **: This desktop file does not exist /usr/lib/awn/applets/plugger.desktop

The program 'avant-window-navigator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 3330 error_code 8 request_code 72 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

I have already tried uninstalling and reinstalling awn and it did nothing as well as restarting my computer. Any help would be much appreciated. I cannot function without avant.

Thanks in advance.

---

### Post by hhhhhx on 2008-02-12
do you have compiz running?

---

### Post by bvc310 on 2008-02-12
I was able to get avant to work by uninstalling and reinstalling compiz. My repositories were incorrect and caused compiz to not function correctly. However, now I have two broken packages, awn-core-applets-bzr and python-libawn-bzr, in synaptic and I recieve an error message when trying to install them that reads ```
E: /var/cache/apt/archives/libawn-bzr_0.2.0-bzr158-1_i386.deb: trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
```
Awn is now fully functioning but there are still these broken packages. I think the problem lies with libawn-bzr and I keep getting that error when trying to install or uninstall the package.

Thanks,

---

### Post by nikoPSK on 2008-02-12
tip: best to post on reacocard's guide. :)

---

### Post by zyvx on 2008-02-18
I have the exact same problem and I have not been able to find the solution. Wierd thing is that AWN is running fine,

Found the solution. I was using a combination of repo and bzr AWN. ooops. Anyway im running perfectly.

---

### Post by prince_niceguy on 2008-02-21
yup i had the same problem. got rectifiied after installing the applets-bzr. seems the repos does not have applet files.

---

