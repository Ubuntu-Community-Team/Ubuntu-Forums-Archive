---
title: "Change 'Show Desktop''Window' and 'Trash' icons ?"
date: 2009-07-23
forum: Desktop Environments
---

### Post by crownedzero on 2009-07-23
How does one go about changing these out?

---

### Post by jerrrys on 2009-07-23
change them out to what?  need a bit more info

---

### Post by brianfactors on 2009-07-23
If you want to change the theme icons, you can go to System > Preferences > Appearance. Click "Customize" and then under "Icons" you can adjust the THEME, but if you want to change two specific icons... I'm not quite sure were to go. It'd be somewhere in /usr/share/icons.

Ok, using locate and grep (command line stuff for finding files).
```
locate user-desktop.png
```
```
locate user-trash.png
```

(Type these into the command terminal) The output of these commands should tell you were to look. I'll be something like:
/usr/share/icons/Human/16x16/places/user-desktop.png

There really is no simple way to change these. If you're really convinced that that's what you want to do, you'll have to change 'em by hand. Messy stuff. Why would you want to change 'em anyway?

---

### Post by crownedzero on 2009-07-23
I've updated my desktop theme and all of my regular icons have been updated, excluding the "Show desktop"(bottom left) and two in the bottom right "Trash" and the desktop 1 and 2 switch. I've seen these icons swapped in several UIs. I was curious how it was done. See attached.

---

### Post by mcduck on 2009-07-23
> **crownedzero said:**
> I've updated my desktop theme and all of my regular icons have been updated, excluding the "Show desktop"(bottom left) and two in the bottom right "Trash" and the desktop 1 and 2 switch. I've seen these icons swapped in several UIs. I was curious how it was done. See attached.

Trash and Show Desktop-icons will definitely change if you change your icon theme. (You sometimes have to log out and back again or reload gnome-panel to ge tthe trash icon to change to new theme). I'm not sure how many themes really have icn for the Show Desktop-applet as I'm not using the applet myself.

The workspace Switcher-applet doesn't have any icons, it simply gets the colors it uses directly from your GTK theme.

---

### Post by jerrrys on 2009-07-23
here's half an answer...also i have not myself tried this so use at your own risk...

[ATTACH]122205[/ATTACH]

---

### Post by crownedzero on 2009-07-30
Thanks guys

---

