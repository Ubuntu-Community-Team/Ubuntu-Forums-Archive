---
title: "lucid:  &quot;move to desktop right&quot; with Wine causes window to disappear"
date: 2010-04-19
forum: Desktop Environments
---

### Post by TheKorn2 on 2010-04-19
Anyone know how to reset gnome's defaults regarding which virtual desktop a new window launches in?



Here's what happened...  I use wine to run the xnews newsreader.  For some reason I right clicked on the title bar one night and threw it one desktop to the right.  I don't remember what happened after that, but it didn't "look right" on the desktop to the right.  So I threw it back one desktop to the left, where it began.

Except now when I launch xnews, the launch effect happens and now NO window shows on ANY desktop!  It's really running...

```
~$ ps aux | grep xnews
vince    12012  2.7  0.5 2658860 10852 ?       S    07:59   0:00 /home/vince/xnews/XNEWS.EXE
```

...but shows *no* windows, on any of the four default desktops.

I've tried doing an apt-get purge, I deleted ~/.wine/* , but that didn't help.

My only guess is that gnome is somehow "remembering" something from this (maybe which "desktop" it's supposed to show up on?) and it's been corrupted.

So how do I reset gnome's data for launching an application, with regards to window and virtual desktop placement?

(If anyone has any better ideas, I'm open to those as well!)

Thanks!

---

### Post by 3Miro on 2010-04-19
Have you tried Alt + Tab or some of the other commands that show all the running windows. Sometimes Gnome and Compiz will be out of sync on the panel taskbar and the actual windows running.

---

### Post by TheKorn2 on 2010-04-19
> **3Miro said:**
> Have you tried Alt + Tab or some of the other commands that show all the running windows. Sometimes Gnome and Compiz will be out of sync on the panel taskbar and the actual windows running.

I hadn't, but I just tried it now.  Nope, nada; even though the process is running no window appears to switch to when I hit alt-tab.

(Tried it on all four virtual desktops, just to be safe.)

---

