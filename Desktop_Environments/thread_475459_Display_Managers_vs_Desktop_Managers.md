---
title: "Display Managers vs Desktop Managers"
date: 2007-06-16
forum: Desktop Environments
---

### Post by B-Con on 2007-06-16
I just want to see if I have this straight thus far:

Display managers are not the same thing as desktop managers. Display managers manage the graphical interface the user sees (windows, colors, corners, etc). Whereas desktop managers take care of your desktop, your file browser, etc. (Would Gnome be a display manager and Metacity be a desktop manager?)

That said (assuming that's correct), can you mix and match display managers with desktop managers to your liking?

---

### Post by moore.bryan on 2007-06-16
[i]for linux, x is the display manager and then gnome/kde/enlightenment/fluxbox/openbox/etc. are the desktop environments (managers).

these two articles may clear things up:
[x display manager]("http://en.wikipedia.org/wiki/Display_manager")
and
[desktop environment]("http://http://en.wikipedia.org/wiki/Desktop_manager")
[/i]

---

### Post by B-Con on 2007-06-16
Thanks. So... 

GNOME is a Desktop Manager. Metacity is a Window Manager.

Fluxbox is a Desktop Manager. ROX is a... Window or Desktop Manager?

So, when I install Fluxbox and the [desktop is bare](http://ubuntuforums.org/showthread.php?t=449278) (with nothing on it), I was told I need to install a desktop manager like iMenu since Fluxbox doesn't come with that. Obviously the correct term for it isn't "desktop manager" since Fluxbox is a desktop manager, so what is Fluxbox missing that controls the desktop?

Just trying to get the whole what-depends-on-what topology straight.

---

### Post by Nythain on 2007-06-17
Display manager - X, KDM, GDM, others
Desktop Environment - KDE, Gnome, xfce
Window Manager - Kwin, Metacity, Emerald, Aquamarine, xfce, fluxbox

ROX, in a class of its own, right up there with E17/Enlightenment... they blend the boundries a little bit

---

### Post by B-Con on 2007-06-17
So, is Fluxbox not a Desktop Environment? Thus if I wanted to use Fluxbox, I would need a Desktop Environment to go with it(?).

---

### Post by Nythain on 2007-06-17
[http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/)

you can run it solo, using x, for a minimal desktop experience, or within other DE's...
heres some example screenshots
running with rox:
[http://www.lynucs.org/index.php?screen_id=182161973940caf31fa66dd&p=screen](http://www.lynucs.org/index.php?screen_id=182161973940caf31fa66dd&p=screen)

running with kde:
[http://www.lynucs.org/index.php?screen_id=161492268346522bb3cb55a&p=screen](http://www.lynucs.org/index.php?screen_id=161492268346522bb3cb55a&p=screen)

running with gnome:
[http://www.lynucs.org/index.php?screen_id=3502925234640ff08e124c&p=screen](http://www.lynucs.org/index.php?screen_id=3502925234640ff08e124c&p=screen)

running with xfce:
[http://www.lynucs.org/index.php?screen_id=1018895466461ef2adbcf0b&p=screen](http://www.lynucs.org/index.php?screen_id=1018895466461ef2adbcf0b&p=screen)

---

### Post by RedSquirrel on 2007-06-17
> **B-Con said:**
> So, is Fluxbox not a Desktop Environment? Thus if I wanted to use Fluxbox, I would need a Desktop Environment to go with it(?).

You don't need a separate DE. Fluxbox is "only" a window manager, but you can still use it by itself (once you generate the menu!). 

If you want desktop icons, idesk is one possibility.

fbpanel will give you a more advanced panel in place of the standard Fluxbox toolbar.

conky or gkrellm will give you a system monitor.

Check out the Howto in my sig for some ways to make a custom menu.

See the Fluxbox site and the Fluxbox wiki for more ideas on customizing your Fluxbox:

[ fluxbox.org]("http://fluxbox.org")
[ flubox-wiki.org]("http://flubox-wiki.org")

I tend to leave my Fluxbox fairly plain. ;)


EDIT:

Here's a Howto for rox if you want to give that a try:

[http://community.fluxbuntu.org/index.php/topic,78.0.html](http://community.fluxbuntu.org/index.php/topic,78.0.html)

---

