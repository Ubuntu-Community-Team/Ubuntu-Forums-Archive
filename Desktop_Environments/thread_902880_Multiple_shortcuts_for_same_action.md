---
title: "Multiple shortcuts for same action"
date: 2008-08-27
forum: Desktop Environments
---

### Post by bluegray on 2008-08-27
Is there some way to have multiple shortcuts for the same action? Eg. <Ctrl>+<Alt>+P and the play/pause button on the keyboard to do the same thing.

---

### Post by mirko_3 on 2008-11-09
Yeah I really wanna know too, i've been trying to bind a mouse button to "move window" for a while, in addition to "alt+button1" which i already have in ccsm

---

### Post by excalq on 2011-07-13
Resurrecting this ancient thread to ask the same. I'm running classic gnome (metacity), and would love to use the multimedia keys on my home office keyboard, but have backups for when the laptop is elsewhere. Specifically, I'd like to assign "CTRL+ALT+LEFT" AND "XF86Back" to switch workspace left, etc.

Any answers?

---

### Post by stehpanka on 2011-12-30
I'm trying the same with Ubuntu 11.10 Oneiric Ocelot, "gnome classic".
Pressing the multimedia buttons on my laptop works as expected.
In the "System Settings" -> "Keybord"->"shortcuts" the shortcuts for "next title"/"play"/etc are mapped the XF86Audio Keys.
Unfortunately my real (USB-)Keyboard lacks those Multimedia buttons.
So i defined my own shortcut:
<Shift>Page_Down
to run the command "xdotool key XF86AudioNext" or "xte "key $(gconftool -g /apps/gnome_settings_daemon/keybindings/next)"" or "xte 'key XF86AudioNext'".
But Banshee, my media player, does not react when I press Shift+PageDown.
On the other hand, all three commands behave as expected when executed from a terminal: Banshee jumps to the next title.
Furthermore my system is able to detect Shift+PageDown: If i change the command to "gedit" the text editor is opened when pressing Shift+PageDown.
So. What is going on here?

How can I map multiple shortcuts to the same action?

stehpanka

---

### Post by fulopattila122 on 2012-01-20
It seems that it's not possible unless you're ready to edit the esoteric xmodmaprc file in your home directory.

That way it's possible as described here:
[http://ubuntuforums.org/showthread.php?t=1207221](http://ubuntuforums.org/showthread.php?t=1207221)

I've been working with Linux for 10+ years, still I didn't have the humor to start that thing. Good luck :)

---

