---
title: "KDE System Tray icons &quot;sometimes&quot; too big"
date: 2007-11-14
forum: Desktop Environments
---

### Post by Zorael on 2007-11-14
I'm running Kubuntu 7.10, and when launching some specific programs their system tray icons sometimes end up at ~twice the size. This causes the tray to display only one row of icons instead of the two I want it to.

The programs that cause this are Pidgin and Xchat, if that helps.

Is there someway to force it to always have a specific icon size? Perhaps a replacement systray applet?

---

### Post by Fry-kun on 2007-12-20
I'm having the same problem (using Fedora Core 6 and Fedora 8, KDE 3.5).
The most frequent one is pidgin, though sometimes it's nm-applet (seems that in fedora 8 kde-networkmanager doesn't exist yet) - and other times PulseAudio applet.
I suspect the common thing between all these is that they're all made for gnome, not KDE - though I'm not 100% sure.
No idea how to fix it. It annoys the hell out of me, but then I just log out and back in - and it shows up correctly.

---

### Post by MattBD on 2007-12-29
> **Fry-kun said:**
> I'm having the same problem (using Fedora Core 6 and Fedora 8, KDE 3.5).
The most frequent one is pidgin, though sometimes it's nm-applet (seems that in fedora 8 kde-networkmanager doesn't exist yet) - and other times PulseAudio applet.
I suspect the common thing between all these is that they're all made for gnome, not KDE - though I'm not 100% sure.
No idea how to fix it. It annoys the hell out of me, but then I just log out and back in - and it shows up correctly.

I'm having the same problem as well, although I've found Pidgin isn't too bad. The main offender in my case is Google Desktop Linux. I think this is very likely intended more for Gnome than KDE, as you said, since I downloaded from Google's Ubuntu repository.

---

### Post by harold4 on 2008-05-16
When I open pidgin, I use the following script.  It's ugly, but it works.  
```

#!/bin/sh
pidgin
dcop kicker Panel setPanelSize 24
dcop kicker Panel setPanelSize 54

```

---

### Post by jcholewa on 2008-07-09
Here's one solution:
Go to "/usr/share/pixmaps/pidgin/tray/".  You'll need root access to do stuff here.
This contains the tray icon images for pidgin, organized by size.  Look in the subdirectories and find the largest size icons you'd like to see on your system tray.  Then backup the larger ones and make a symbolic link from the largest acceptable icon size directory to the larger directory names.

For example, I did "mv 48 .48; mv 32 .32" to backup the "48" and "32" size icons.  Then I did "ln -s 22 32; ln -s 22 48".  Now whenever it tries to grab the 32x32 icons or the 48x48 icons, it'll just find the 22x22 icons, and that's what it'll show.

Been working fine since I did this.  Not a fix but a workaround.  Should work for other apps, too.

---

### Post by m0sh3g on 2008-07-17
I've noticed that running knowit with systray icon enabled, will reset the sizes of icons including pidgin :)

---

