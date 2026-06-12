---
title: "Beryl working, but old Gnome look for controls (buttons, etc.)"
date: 2006-11-30
forum: Desktop Environments
---

### Post by _davidh on 2006-11-30
Hey.

I'm new to Ubuntu, and I'm really liking it. I've got XGL and Beryl up and running, but for some reason, the controls have the old Gnome look, see screenshot:
[[IMG]http://img171.imageshack.us/img171/2236/screenshotri4.th.png[/IMG]](http://img171.imageshack.us/my.php?image=screenshotri4.png)

During the installation, I got a 404 on xgl.compiz.info. Running **apt-get update** produces the following:

```
...
Failed to fetch http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://xgl.compiz.info/dists/dapper/main/source/Sources.gz  404 Not Found
...
```

Can this somehow be related? If so, are there any alternatives to xgl.compiz.info?

Or does anyone know what else might be the problem?

Thanks in advance for any pointers.

---

### Post by mayonaise15 on 2006-11-30
I copied this text from the beryl-project.org wiki, which can be found [here]("http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/XGL#Troubleshooting")

Help, the window borders are fine, but my window widgets, dialog boxes, icons etc. look funny / not so funny / really grey / very 1990's / like gtk-1 fallbacks. What's up with that?

According to forum posters, there are several ways to solve this issue:

1) Try running gnome-settings-daemon from a terminal:

```
$ gnome-settings-daemon &
```

You should now see the widgets and icons you selected. To run this command at session login, go to System &#8594; Preferences &#8594; Sessions, go to the "Startup Programs" tab, click the "Add" button and type gnome-settings-daemon into the dialog box.

2) If you are using the startxgl.sh script described above and if you are using GNOME, try replacing the final command exec gnome-session with exec dbus-launch --exit-with-session gnome-session

```
#!/bin/sh
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session
```

3) Disable Beryl's splash screen in Beryl Settings Manager.

---

### Post by _davidh on 2006-11-30
mayonaise15, you are the man.

Running gnome-settings-daemon worked like a charm. I haven't tried the login stuff yet, but I'm sure they'll work.

Big thanks :-)

---

### Post by mayonaise15 on 2006-11-30
Hehe, glad it worked for you.  I had the same problem a couple of weeks ago and it drove me nuts!

---

