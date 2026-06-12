---
title: "Unity minimize bug?"
date: 2013-10-21
forum: Desktop Environments
---

### Post by David_OConnor on 2013-10-21
I'm running Ubuntu 13.10. Often when I have multiple windows of the same type open, when I click their Unity icon twice to select windows, only one window will show. The rest will have a space on the screen and can be highlighted by mousing over, or clicking, but they are invisible.

This would be better demonstrated with a screenshot, but I can't figure out how to take screenshots (print screen's not working, and the screenshot app doesn't do anything). Here's a Gimp-drawn image instead. Note that the left window outline is only visible when moused over. 

[IMG]http://i.imgur.com/rrd6ifu.png[/IMG]

---

### Post by deadflowr on 2013-10-21
If screenshot is not working then you have bigger problems then window feature issues.

---

### Post by David_OConnor on 2013-10-21
I got the screenshot utility working. Here's a screenshot demonsrating the problem. Note that there are three file explorer ticks on the left indicating three windows open, but only one is displayed. When the mouse is moved over where the other windows should be (it's currently over the left window), the window highlights, and can be selected with a click.

[ATTACH=CONFIG]247115[/ATTACH]

[http://i.imgur.com/S1CFoRW.jpg](http://i.imgur.com/S1CFoRW.jpg)

---

### Post by coffeecat on 2013-10-21
Support question, not chat.

*Thread moved to **Desktop Environments**.*

---

### Post by David_OConnor on 2013-10-25
Bumping this - I can't be the only one.

---

### Post by vanadium on 2013-10-25
Most likely an issue with your graphics driver. You may want to try some of the opengl or composite related settings in Compiz Config Settingsmanager to see whether that cures the issue, e.g. "Composite": try disabling (or enabling if for you off by default)) "Detect refresh rate", in "Opengl" try disabling (or enabling) "Sync to vblank".

---

### Post by David_OConnor on 2013-11-08
This bug appears to be fixed by a ubuntu system update yesterday.

edit: Not fixed, coincidence. I even did a clean format/install for other reasons, and the bug still exists.

---

