---
title: "Terminal command for Customize Look and Feel"
date: 2013-04-04
forum: Desktop Environments
---

### Post by Apolyonn on 2013-04-04
Hey all,

I've been using Lubuntu/Openbox for awhile now.  I really like the tint2 configuration on #!, and I've been using its config file with tint in Lubuntu.  However, in removing the stock taskbar, I lost my menu button, and have no idea how to launch the customize look and feel window.

Does anyone know what the command is for this in a terminal?

Thanks

---

### Post by cortman on 2013-04-04
You probably want

```
lxappearance
```

---

### Post by Apolyonn on 2013-04-04
> **cortman said:**
> You probably want

```
lxappearance
```

Exactly what I wanted.  Thanks a bunch.

Also, I feel really stupid for asking this, but I cannot remember how to mark a thread as "SOLVED."

---

### Post by cortman on 2013-04-04
No problem. Glad to be of help. :)
Don't feel stupid- the plugin doesn't work with the new version of VB (yet). Just edit the original post and add [SOLVED] to the front of the thread.
Good luck!

---

### Post by vasa1 on 2013-04-04
> **Apolyonn said:**
> ...
Does anyone know what the command is for this in a terminal?
...
Here's something, not limited to Lubuntu, that gives you both the descriptive name of a program as well as the command to invoke that program in a terminal as Name and Command pairs:
```
sed -nrs '/^\[Desktop Entry\]/d;/^(\[|Name=|Exec=)/p;${g;p}' /usr/share/applications/*.desktop > ~/Desktop/a1.txt
```This code creates a file called a1.txt on your desktop and it looks like this, in part:
```

...
Name=Shutdown
Exec=lubuntu-logout

Name=ScreenLock
Exec=xscreensaver-command -lock

Name=Lubuntu Software Center
Exec=lubuntu-software-center

Name=Customize Look and Feel <<<<<<<<<<<<<<<<<<
Exec=lxappearance

Name=Terminal emulator
Exec=/usr/bin/x-terminal-emulator

Name=Web Browser
Exec=/usr/bin/x-www-browser %u

Name=Keyboard and Mouse
Exec=lxinput

Name=Lxkeymap
Exec=lxkeymap
...

```

By its nature, it's limited to programs with .desktop files located in /usr/share/applications only. I can't explain the order in which the names and command pairs appear and so the name or command pair may not appear in strict alphabetical order. (The code above is slightly modified from that [here]("http://ubuntuforums.org/showthread.php?t=2124743&p=12554090#post12554090").)

---

### Post by cortman on 2013-04-05
Hey, very nice one-liner there, vasa1.

---

