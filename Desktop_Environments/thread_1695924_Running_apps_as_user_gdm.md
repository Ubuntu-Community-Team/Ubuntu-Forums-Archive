---
title: "Running apps as user gdm"
date: 2011-02-26
forum: Desktop Environments
---

### Post by towheedm on 2011-02-26
In Karmic, I could run an app as user gdm by issuing the following command (assume the app is gconf-editor)

```
gksudo -u gdm dbus-launch gconf-editor
```Now that I've switched to Marverick when I issu the same command I get this:

```
towheed@GA1A4CH:~$ gksudo -u gdm dbus-launch gconf-editor
No protocol specifiedNo protocol specified

** (gconf-editor:19812): CRITICAL **: Failed to parse arguments: Cannot open display:
```I checked my environment variable DISPLAY using:

```
towheed@GA1A4CH:~$ echo $DISPLAY
```and it returned:
```

:0.0
```Now I ran the command:

```
gksudo -u gdm dbus-launch gconf-editor --display=:0.0
```and got the same error as before.

Has either or both dbus-launch or gksudo changed their behavior os is this a bug.  Note that the command does not work with any applications being run as the user gdm.

Can anyone help me?

---

### Post by Krytarik on 2011-02-26
Seems to have change from Maverick onwards, try this:
[http://ubuntuforums.org/showthread.php?p=10418202](http://ubuntuforums.org/showthread.php?p=10418202)

---

### Post by towheedm on 2011-02-26
Yep, that worked.  What I did wrong was to add the localhost to the xhost instead of the localuser.

Thanks.

---

