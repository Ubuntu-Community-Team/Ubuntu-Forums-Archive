---
title: "GTK apps in the KDE system tray - unreadable text"
date: 2007-11-16
forum: Desktop Environments
---

### Post by TeeAhr1 on 2007-11-16
See the screenshot.  KDE apps in the system tray have black text, but GTK apps have white text which is completely unreadable on the yellow background.  I can't find an option for changing either the tooltip background color or the text anywhere.  Does anyone know how to do this?

---

### Post by TeeAhr1 on 2007-11-16
bump

---

### Post by TeeAhr1 on 2007-11-18
bump

---

### Post by aatiis on 2007-11-26
Well, my GTK apps have the same tooltips as KDE ones. On the other hand, they have a white background. Very odd, but not unusable. Do **all** of your GTK apps behave like that? Which KDE version? (I'm running KDE 3.5.8 on Kubuntu Gutsy.)

---

### Post by pointfivezero on 2007-11-26
> **TeeAhr1 said:**
> See the screenshot.  KDE apps in the system tray have black text, but GTK apps have white text which is completely unreadable on the yellow background.  I can't find an option for changing either the tooltip background color or the text anywhere.  Does anyone know how to do this?

 I'm certain this applies to all GTK apps running under KDE (see below) because I only see this white on light-yellow-impossible-to-read horror in, for example; compiz config settings manager, GIMP.

 UPDATE: The gtk-qt engine IS the culprit, or to be more precise (correct me if I am wrong though), gtk in general!

**To get tooltips show correctly at the expense of gtk/kde colour uniformity** add the following lines to your ~/.gtkrc-2.0-kde file:
```

style "user-colours"
{
  bg[NORMAL]="#efefef"
  fg[NORMAL]="#000000"
}
widget "*" style "user-colours"

```

I know that this seems very broad but this is however the only way for me to change the tooltip colours.

EDIT: I had installed the very latest version of gtk-qt-engine but the issue still remains.


Cheers

---

### Post by pointfivezero on 2007-11-26
I believe the solution would be working out the entries for ~/.gtkrc-2.0-kde or a patch in gtk that seperates the tooltips colouring from the text (?) widgets.

---

### Post by tremby on 2008-05-17
i'm having this problem too. the workaround suggested seems to affect tooltips in some applications but not others, and where it does have an effect the background is never affected.

i'd guess from this that in some GTK applications the tooltip text colours are hardcoded but not in others. and i don't know what to make of the fact that the background colours aren't affected -- is the tooltip background colour hardcoded in all apps? seems ridiculous...

---

