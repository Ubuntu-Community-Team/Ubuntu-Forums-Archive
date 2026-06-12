---
title: "A couple of further problems"
date: 2006-04-14
forum: Desktop Environments
---

### Post by Rhapsody on 2006-04-14
Now I've finally got Kubuntu up and stable. I'm very happy with it and I think we'll have a long and... interesting relationship. But there are a couple of things with it that have got me stumped.

First is the clock. It's brilliant thing, far superior to the Windows XP clock, but it's an hour fast for some reason. In the installer, it displayed the system time (which was more or less correct) and asked me if the clock was set to GMT. I live in England, so I said yes. But when I'm in Kubuntu, the clock is an hour fast for some reason. This applies equally if I select 'Local Timezone', 'Europe/London', or 'Europe/Belfast'. I do think when it asked me if the clock was set to GMT, it may have been asking me about daylight saving time. If so, how on earth do I fix this now?

Second, screenshots. I want to take a good screenshot of the desktop so other people on my regular forums will actually believe I've gone and installed Linux. But although most Windows key combinations seem to be the same here, Print Screen doesn't. What do I use for this?

---

### Post by aysiu on 2006-04-14
[QUOTE=Rhapsody]
First is the clock. It's brilliant thing, far superior to the Windows XP clock, but it's an hour fast for some reason. In the installer, it displayed the system time (which was more or less correct) and asked me if the clock was set to GMT. I live in England, so I said yes. But when I'm in Kubuntu, the clock is an hour fast for some reason. This applies equally if I select 'Local Timezone', 'Europe/London', or 'Europe/Belfast'. I do think when it asked me if the clock was set to GMT, it may have been asking me about daylight saving time. If so, how on earth do I fix this now?[/quote] [This](http://ubuntuforums.org/showthread.php?t=6285) may help.

> 
Second, screenshots. I want to take a good screenshot of the desktop so other people on my regular forums will actually believe I've gone and installed Linux. But although most Windows key combinations seem to be the same here, Print Screen doesn't. What do I use for this? The KDE program for screenshots is called KSnapshot. Make sure you have that installed. Then right-click on the KMenu, edit the menu, find the entry for KSnapshot. In the bottom-right-hand corner, there's a place to define a keyboard shortcut for it.

---

### Post by Rhapsody on 2006-04-14
[QUOTE=aysiu][This](http://ubuntuforums.org/showthread.php?t=6285) may help.[/QUOTE]
That looks good. I'm nervous to try it considering how I totally screwed up my last install (about four hours ago) but I'll have to get around to that.

[QUOTE=aysiu]The KDE program for screenshots is called KSnapshot. Make sure you have that installed. Then right-click on the KMenu, edit the menu, find the entry for KSnapshot. In the bottom-right-hand corner, there's a place to define a keyboard shortcut for it.[/QUOTE]
That worked perfectly. It's even better than Print Screen. Thanks.

---

### Post by Rhapsody on 2006-04-14
I finally tried the command suggested for getting my time back on track, but all I got was "sudo: gedit: command not found". Is this something to do with me using Kubuntu rather than Ubuntu?

---

### Post by aysiu on 2006-04-14
Sorry.

Gedit is a Gnome text editor.

Translate that to be ```
sudo kwrite
``` instead of ```
sudo gedit
```

---

