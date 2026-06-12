---
title: "How to set themes for individual applications?"
date: 2006-03-25
forum: Desktop Environments
---

### Post by GameManK on 2006-03-25
Hi,

I like the basic plastik theme for most of my apps, but I want something fancier like baghira for amaroK.  How can I set a theme for an individual application?

It just seems like something that KDE would be able to do...

---

### Post by GameManK on 2006-04-13
?
bump

---

### Post by RS3York on 2006-04-14
Hmm, I'm not sure about this one.

I do know that within the Baghira theme you can setup individual apps to have their own look.  Baghira is pretty flexible in its own right so that may be enough.

But you seem to want pure separate themes...I'm sure it's *possible*, now how *easy* it is to do...that's another ballgame.

---

### Post by bvc on 2006-04-15
does kde have a file for theme defaults? Gnome uses ~/.gtkrc-2.0 and for a specific theme for a specific app
GTK2_RC_FILES=~/.themes/Olive/gtk-2.0/gtkrc gedit

just thought I might point a kde user in the right direction and give the answer for gnome users before someone asked.

---

### Post by GameManK on 2006-04-18
There is a similar file (i think) ~/.qt/qtrc that contains:
```
[General]
GUIEffects=general^eanimatecombo^e
embedFonts=true
enableXft=true
font=DejaVu Sans,9,-1,5,50,0,0,0,0,0
fontPath=\0
style=lipstik
useXft=true
```
and some other stuff that seems irrelevant but I don't think there's anything there for individual applications.

There is also a ~/.kde/share/config/amarokrc but that doesn't contain any style/theme info, I think it's just session info.

---

### Post by GameManK on 2006-04-18
Also for every window and application in KDE there are "special window settings" and "special application settings".  I would think those would give you the option of changing the theme, but there's only geometry related stuff in there.

---

### Post by GameManK on 2006-05-02
I found that you can set the style of any KDE application by launching it with "--style=yourstyle"
for example:
amarok --style=baghira

Does anybody know a similar option for changing the window decoration?

---

