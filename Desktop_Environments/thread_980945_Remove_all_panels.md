---
title: "Remove all panels"
date: 2008-11-13
forum: Desktop Environments
---

### Post by Foxblood on 2008-11-13
Hi, all,

I've seen this issue addressed in other threads but no satisfactory, conclusive answer to the problem. I want to remove the panels, including the last panel with 'delete this panel' greyed out. I've seen how to hide it but not how to remove it. I'm using AWN and have no need for Gnome panels.
Anyone?

Thanks in advance.

---

### Post by binbash on 2008-11-13
I am also looking for a solution except moving gnome-panel command

---

### Post by TFX360 on 2008-11-28
1. Goto System -> Preferences -> Sessions

2. Click on Current Session tab. Find gnome-panel there and set it's style to "Trash" and click Apply button. DO NOT close the Sessions Window.

3. Now open a terminal

```
sudo killall gnome-panel
```

4. Now close the terminal window and go back to the sessions window.

5. Click on the Session Options tab and check (tick) the "Automatically remember running applications when logging out" check-box.

6. Click on the "Remember currently running applications" button.

7. Close the sessions window.


Tada!


TFX

---

### Post by squee on 2008-11-28
Have you removed and unlocked everything on the tool bar? Then try to remove it.

I've never tried it, but that could be a way to do it. A lot of items on the default bar are locked like the menu, FF buttons, power button etc. Unlock them and remove.

---

### Post by TFX360 on 2008-11-28
> **squee said:**
> Have you removed and unlocked everything on the tool bar? Then try to remove it.

I've never tried it, but that could be a way to do it. A lot of items on the default bar are locked like the menu, FF buttons, power button etc. Unlock them and remove.

Dit that, but you can't remove the last panel!

---

### Post by ripzippysf on 2009-11-03
I'm running 9.10 Karmic and I can't figure out how to remove the last panel either.  I just have a blank panel that is a waste of space.  All the instructions I see are for Jaunty.  Anyone know the exact steps to remove the last panel in the Karmic release?

---

### Post by gregbzh on 2009-12-14
> **fagmango said:**
> I'm running 9.10 Karmic and I can't figure out how to remove the last panel either.  I just have a blank panel that is a waste of space.  All the instructions I see are for Jaunty.  Anyone know the exact steps to remove the last panel in the Karmic release?
Ditto.  I've tried everything but still have one panel that reappears.  Any ideas anyone?

---

### Post by sisco311 on 2009-12-14
press Alt+F2 and run:
```

gconf-editor
```
go to desktop/gnome/session/required_components and delete the value of *panel* (which is set to gnome-panel by default).

---

### Post by n4pgw on 2009-12-15
"You can't remove the last panel"  Someone, please tell my daughter that.  She just deleted the panel and now I have no access to anything except the terminal shortcut on the desktop.

I just posted a request for help.

LOL, leave it to a 22 month old baby to get past man's best locks. 

Buck

---

