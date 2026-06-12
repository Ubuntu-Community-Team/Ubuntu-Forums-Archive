---
title: "Unable to unhide hidden panel"
date: 2009-11-16
forum: Desktop Environments
---

### Post by lgp171188 on 2009-11-16
Hi,
I tried to create a panel that autohides on the left side of my desktop. But once it got hidden, I am unable to unhide it though I push my mouse to the leftmost position possible. I don't want to kill the gnome-panel process for this purpose. Are there any ways/commands/workarounds for resolving this issue? 

P.S. I use Karmic with Gnome.

---

### Post by AlphaLexman on 2009-11-16
Are the 'hide" buttons visable? They may be underneath the top and/or bottom panels. If not make sure you have all your desktop switching modes turned off. Sometimes moving the cursor to the left of the screen will take you to the leftmost desktop. This is usually a compiz or other window decoration manager setting.

The important part is to figure out what setting or panel is preventing you from unhiding your panel.

Good luck

---

### Post by spacebar22 on 2010-01-05
I have the same problem on 9.10 with Gnome. I autohid two "taskbars" that were one above the other. On reboot I have a fixed single empty "taskbar", dragging or right-clicking which has no effect. I can open Nautilus by right-clicking a file but can't launch a program (I need Terminal I guess) even with Create Launcher because it wants a command without telling you what the launch command is. The Help button doesn't help indeed suggests you don't need a command whereas there is an error if you don't give one.         

So it seems there is no way out except reinstall?  Please give step by step how I might be able to get back the menus that used to be on the taskbar - thanks

---

### Post by cometdog on 2010-01-19
Can you run gconf-editor?  You can run it from the terminal or from Alt+F2.  I don't recall if it's installed by default.  If not, you can always
```
sudo apt-get install gconf-editor
```
If you can't figure out how to get to a terminal, you should be able to get one by running gnome-terminal from Alt+F2.
Then navigate in gconf-editor to
/apps/panel/toplevels/
and find your problematic panels in there.  You can change the properties directly in the right-hand pane on the editor.

HTH

---

### Post by Lupi on 2010-02-12
Thanks cometdog for your advice. I played with the hide option for the bottom panel and when I minimized it, I couldn't see or access it anymore. So I opened gconf-editor in a terminal and unchecked the "hide" option for the bottom panel.

---

### Post by henriquemaia on 2010-05-30
> **cometdog said:**
> Can you run gconf-editor?  You can run it from the terminal or from Alt+F2.  I don't recall if it's installed by default.  If not, you can always
```
sudo apt-get install gconf-editor
```
If you can't figure out how to get to a terminal, you should be able to get one by running gnome-terminal from Alt+F2.
Then navigate in gconf-editor to
/apps/panel/toplevels/
and find your problematic panels in there.  You can change the properties directly in the right-hand pane on the editor.

HTH

Thanks for this help. Thanks to this, I was able to unhide the stubborn panel and to configure in ways I wasn't even aware before.

I found there a way to configure the size of the hidden panel, which in turn allowed overcome my original problem of not being able to unhide the auto-hidden panel.

---

### Post by nitrooreo on 2010-07-18
One explanation for this behavior here: [https://bbs.archlinux.org/viewtopic.php?pid=394617]("https://bbs.archlinux.org/viewtopic.php?pid=394617")

> turns out if you have any vertical desktops in compiz (at least with the desktop wall plugin) it wont recognize the bottom, maybe because compiz expects you to drag and drop windows over the border...

---

### Post by lgp171188 on 2011-09-14
> **henriquemaia said:**
> Thanks for this help. Thanks to this, I was able to unhide the stubborn panel and to configure in ways I wasn't even aware before.

I found there a way to configure the size of the hidden panel, which in turn allowed overcome my original problem of not being able to unhide the auto-hidden panel.
Thanks, I was able to solve the problem with your guidance. :)

---

