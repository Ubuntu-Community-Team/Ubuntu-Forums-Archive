---
title: "take a screenshot under XFCE"
date: 2011-03-28
forum: Desktop Environments
---

### Post by cccc on 2011-03-28
hi

I have Xubuntu with a minimal XFCE 4.6 installed.
Howto take a screenshot under XFCE?

---

### Post by slooksterpsv on 2011-03-28
Go to XFCE Menu -> Accessories -> Screenshot

---

### Post by Jose Catre-Vandis on 2011-03-29
Or simply press the PrtSc (Print Screen) key - this should pop up a dialog to save a file of your screen shot

---

### Post by cccc on 2011-03-29
Thx, but my problem is I have a minimal XFCE 4.6 installed.
I don't have XFCE Menu -> Accessories -> Screenshot and PrtSc (Print Screen) key doesn't work.
What's missing?

---

### Post by 3Miro on 2011-03-29
The screen-shot is actually a plugin for XFCE panel.

```
sudo apt-get install xfce4-screenshooter-plugin
```
(or use Synaptic)

Then you should get the menu entry (you may have to add it to the panel).

---

### Post by cccc on 2011-03-30
Thx, I have installed xfce4-screenshooter-plugin and howto configure now, that **PrtSc (Print Screen) key** will work as well?

---

### Post by 3Miro on 2011-03-30
Check if the menu has "take screenshot option now". To get the PrtScn button working, you need to right-click on either the top or bottom panel, select "add" and then add the screenshooter applet.

---

### Post by cccc on 2011-03-30
I have in the menu "take screenshot option now" , but I'd like to get this working just pressing PrtScn key from the keyboard. 

BTW Knows someone, howto add this in .config/xfce4/xfconf/xfce-perchannel-xml/**xfce4-keyboard-shortcuts.xml** manually?

---

### Post by 3Miro on 2011-03-30
Right-click on your panel, select "add" and then add a screenshooter-plugin. This should work.

Also if the command is:
```
xfce4-screenshooter -f
```
and if the command works, then you can add that to the keyboard shortcuts. Go to Setting Manager -> Keyboard -> Application Shortcuts and add the command. You can bind the command to any key that you want.

---

### Post by cccc on 2011-03-30
> **3Miro said:**
> Go to Setting Manager -> Keyboard -> Application Shortcuts and add the command. You can bind the command to any key that you want.

Thx, I've add and it works well now.

---

### Post by 3Miro on 2011-03-30
If you have no more questions on this topic, please mark the thread as "solved".

---

### Post by KegHead on 2011-03-30
Hi!

This is great!

I'm testing Xubuntu 11.04 on a dell mini 9.

Solves a minor problem.

KegHead

---

