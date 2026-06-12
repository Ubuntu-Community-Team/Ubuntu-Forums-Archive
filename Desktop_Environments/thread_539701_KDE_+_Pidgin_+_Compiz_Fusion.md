---
title: "KDE + Pidgin + Compiz Fusion"
date: 2007-08-31
forum: Desktop Environments
---

### Post by explemonk on 2007-08-31
I don't know how many people run KDE with Pidgin, but I saw a screenshot somewhere that let me know that at least one other person does. :)

Anyway, I have the Pidgin Message Notification plugin set to flash my taskbar entry when I receive a new message.  It works with Gnome + Metacity, Gnome + Compiz Fusion, and KDE + Kwin, but not KDE + Compiz Fusion.

Has anybody else run across this, and know a solution?

Thanks.

---

### Post by bmorency on 2007-08-31
do you  have a link for the screenshot? I have compiz and kde running with pidgin. do you mean the pidgin icon flashes orange when you get a message or all of the taskbar will flash?

---

### Post by explemonk on 2007-08-31
I don't have a screenshot right now... I will try to post one later.  When I get a message the icon in the system tray changes, no problems there.  But in the window list on the taskbar the entry for Pidgin doesn't change color... The "urgent hint" doesn't seem to be processing correctly, but only when Compiz is running on KDE.  Like I said, it works fine when I have Compiz turned off, and it works fine when I have Compiz running on Gnome.

---

### Post by Zorael on 2007-10-29
Did a solution ever surface for this?

It's still happening for me in Kubuntu 7.10 running Compiz-Fusion from the repositories..

It works if I run kwin instead, but that's no fun.

---

### Post by kenkku on 2007-11-09
I have the same problem. The taskbar flashes with Kopete, but for some reason Pidgin's urgent hint has no effect.

---

### Post by Zorael on 2007-11-09
I was told over at the Compiz Fusion forums that we need a taskbar that is Compiz aware, and was referred to [http://www.kde-apps.org/content/show.php?content=61169](http://www.kde-apps.org/content/show.php?content=61169).

I haven't tried it yet, will do soonish.

(Also [http://www.kde-apps.org/content/show.php?content=46021](http://www.kde-apps.org/content/show.php?content=46021) for a Compiz-friendly desktop pager applet)

---

### Post by Zorael on 2007-11-09
Doesn't seem to work, no difference between it and the standard taskbar.

---

### Post by explemonk on 2007-11-09
> **Zorael said:**
> I was told over at the Compiz Fusion forums that we need a taskbar that is Compiz aware, and was referred to [http://www.kde-apps.org/content/show.php?content=61169](http://www.kde-apps.org/content/show.php?content=61169).

I haven't tried it yet, will do soonish.

(Also [http://www.kde-apps.org/content/show.php?content=46021](http://www.kde-apps.org/content/show.php?content=46021) for a Compiz-friendly desktop pager applet)

I have taskbar-compiz installed.  Doesn't work for me.

Also, it's not necessary to install the modified pager, as KDE's pager works with Compiz as long as the kicker is started after Compiz.

---

### Post by explemonk on 2008-02-26
After further searching with no answer, I have filed a ticket with Pidgin at [http://developer.pidgin.im/ticket/4926]("http://developer.pidgin.im/ticket/4926").

---

