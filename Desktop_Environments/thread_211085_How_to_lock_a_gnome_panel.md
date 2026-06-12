---
title: "How to lock a gnome panel?"
date: 2006-07-07
forum: Desktop Environments
---

### Post by mmcmonster on 2006-07-07
I'm using Ubuntu Dapper w/ the clearlooks theme.  I have one panel at the bottom of the screen and a second on the top of the screen.  Sometimes, for no apparent reason, the panel at the bottom of the screen gets moved to either one of the sides or to the top of the screen.

Is there some way to lock the whole panel (or fixate it, or something) so that it doesn't move?

By the way, I don't think I ever saw the panel on the top of the screen move like this...

---

### Post by Ctrl+Alt+Del on 2006-07-07
happened to me as well a few times. afaik there is no 'fix'

---

### Post by brallan on 2006-09-21
the drag and drop feature of the panels is a terrible idea, and hopefully it could be changed to some kind of right-click menu-based feature, like move to (right/left/bottom/top) 

In any case, there MUST be some way, if someone could recommend something, i'd be greatful, as I'm the computer guy in a house of 30 people and the panels are ALWAYS being moved by drag and drop accidents, which also leads to all of the applets getting scrambled. A total pain in the mouse.

---

### Post by skymt on 2006-09-21
[Sabayon](http://www.gnome.org/projects/sabayon/) can solve this. Install it via Synaptic.

---

### Post by JBA2337 on 2008-04-14
There is an easy way to lock down all the panels at once. Just install Ubuntu Tweak. You can install it from the Synaptic Package Manager (ubuntu-tweak), or if it is not listed go to [http://ubuntu-tweak.com](http://ubuntu-tweak.com). After you install it, a launcher will be in Applications>System Tools.

When you run this program, click on System. There is a checkbox for "Complete lockdown of the panel".

This will do what you asked for.

JBA2337

---

### Post by moogle on 2008-04-29
better solution all
hit Alt-F2 and run gconf-editor

when you run it navigate to 

apps->panel->global

under lock_down click the checkbox 

and restart gnome with Ctrl-Alt-Backspace

much thanks to ##gnome and #ubuntu on irc.freenode.net for help with this one

---

### Post by stanley45 on 2008-05-23
Moogle - thanks that worked great and now I know about the config editor.

stanley

---

### Post by amosbatto on 2008-07-17
Locking the whole panel is not a very good solution to the problem. First of all, most people will never find the option, because they never use gconf-editor. This is an option which should be in the Properties dialog box for the panel. I just want to lock a panel in its position, because it keeps getting accidently moved, but I don't want to lock every item in the panel. There is no way to do this in GNOME. More and more I have become frustrated with GNOME because it keeps limiting my options.

---

