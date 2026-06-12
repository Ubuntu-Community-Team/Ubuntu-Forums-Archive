---
title: "Start and stop X server without logging out"
date: 2012-07-03
forum: Desktop Environments
---

### Post by Stonecold1995 on 2012-07-03
I run many processor-intensive programs on my laptop, and I need every bit of the CPU I can get.  And I was thinking, KDE is very resource intensive, so what if I turn of the graphical desktop when I'm not using the computer, then turn it back on when I need it again.  I was thinking of using "killall plasma-desktop" when I'm leaving the computer and then "plasma-desktop" when I'm on it again, but the problem with that is it doesn't stop all of the X server, just plasma-desktop.  However, using "sudo killall Xorg" and then "startx" causes me to log out and back in, closing programs I need open.  So my question is, how do I stop the graphical environment when I'm away and then start it up again when I get back?  I assume doing this would save a lot of CPU time in the long run.

---

### Post by msammels on 2012-07-03
OK, this is a quick fix. It's not stopping it per say, but it works. Whenever you leave your computer press:

```
CTRL+ALT+F1
```

This will take you to a new tty. To get back to your current tty, press:

```
CTRL+ALT+F7
```

I'm not sure if this would stop resource usage though as it technically still is running. To be honest, as far as I'm away, if you want to close your DE, you do need to stop the X server, which will reset any logins.

---

### Post by Zorael on 2012-07-07
So you want to restart X itself but keep your session? Hm.

The only way I could see this work is if you have a separate X running as server, then another that connects to it. Assuming that you can keep a session running even if the client disconnects (as eg. nomachine NX supports), that should make it possible to restart it while keeping all data. I imagine this restricts you to indirect rendering though, unless you can find some mix where you run certain stuff locally within the client (like video players).

Though to begin with, I'm inclined to think you're overthinking things a bit. If the machine isn't in active use the KDE bits shouldn't really be using a lot of CPU time. If it's akonadi and/or nepomuk that's bothering you, you can disable those outright with some wizardry.

You can also lower the [niceness](http://en.wikipedia.org/wiki/Nice_(Unix)) of the processes in question to let your 'important' program get CPU scheduler priority. This will obviously make them a bit less responsive.
```
$ renice [COLOR="SeaGreen"]**-n 19**[/COLOR] -p $(ps xo pid,comm | grep 'plasma-\|krunner\|akonadi\|nepomuk' | grep -v grep | awk '{ print $1 }')
*# redo with [COLOR="RoyalBlue"]**-n 0**[/COLOR] to restore*
```

If you want to make those programs start with automatically raised niceness, I believe you can copy their .desktop files (from **/usr/share/autostart/** or **/usr/share/applications/** into **~/.local/share/applications/** and modify their '**Exec=**' lines to look like '**nice [COLOR="SeaGreen"]-n 19[/COLOR] *<executable>***'.

An example **~/.local/share/applications/plasma-desktop.desktop**;
```
[Desktop Entry]
Exec=**nice [COLOR="SeaGreen"]-n 19[/COLOR] plasma-desktop**
X-DBUS-StartupType=wait
Name=Plasma Desktop Workspace

*[...]*
```

---

