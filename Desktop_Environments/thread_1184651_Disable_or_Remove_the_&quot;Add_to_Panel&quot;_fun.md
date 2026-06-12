---
title: "Disable or Remove the &quot;Add to Panel&quot; function"
date: 2009-06-11
forum: Desktop Environments
---

### Post by chang5562 on 2009-06-11
How can I disable the "Add to Panel" function on Ubuntu 8.10?  I am setting up a system (with our own application) under the Ubuntu, so I don't want our user to fool around the system by adding more un-necessary.

---

### Post by mcduck on 2009-06-11
Press Alt_F2 and run "gconf-editor" (or start it from a terminal), browse to apps/panel/global and enable the "locked_down"-key.

This will prevent any changes to panel setup, locking the panels to current configuration until you disable the key again.

---

### Post by chang5562 on 2009-06-12
mcduck
Thx.  Apparently very few people set-up such.  Maybe there is a potential disaster somewhere down the road that I did not see. 
Actually the I tried to disable most of shortcut keys and disable them,  I accidentally hit something which should not allow to user to access but I could not reproduce it.  So.

I also tried to disable the Ctrl-Alt-F1~12, which accesses the tty.  Even the solution by adding "DontVTSwitch" "true" in the xorg.conf works, this change won't pass onto a live CD (or Live USB).  the Live version is still able to use the Ctrl-Alt-F1~12 keys.  Do you have a clue how I can disable these shortcut keys, not by change the xorg.conf?  The xorg.conf is device specific.

---

### Post by mcduck on 2009-06-15
> **chang5562 said:**
> mcduck
Thx.  Apparently very few people set-up such.  Maybe there is a potential disaster somewhere down the road that I did not see. 
Actually the I tried to disable most of shortcut keys and disable them,  I accidentally hit something which should not allow to user to access but I could not reproduce it.  So.

I also tried to disable the Ctrl-Alt-F1~12, which accesses the tty.  Even the solution by adding "DontVTSwitch" "true" in the xorg.conf works, this change won't pass onto a live CD (or Live USB).  the Live version is still able to use the Ctrl-Alt-F1~12 keys.  Do you have a clue how I can disable these shortcut keys, not by change the xorg.conf?  The xorg.conf is device specific.

I think you could just disable the TTY's from starting in the first place, at least this in possible on every Linux distro I have tried (although I have no idea how it's done in Ubuntu, something in /etc/default, I'd guess).

Of course this is assuming you are talking about making your own Live-Cd, as nothing you change in your installed system itself is able to limit what live-CDs can do..

(and no, locking the panels shouldn't ever be a problem. In the end you can always just unlock them if you need to and that can be done even without the gconf-editor, as long as you have access to some terminal. I quite often lock the panels when I install Ubuntu on friends computers, I've noticed many people manage to remove stuff from their panels without realizing what they dd. It's easier to let them get a bit more used to the desktop first and then unlock the panel and show what can be done with it..)

You may also want to check Sabayon & Pessulus, which are Gnome's GUI tools for managing user's desktops and locking down different things.

---

### Post by scrooge_74 on 2009-06-15
There are some tutorials that deal with the specifics or disabling other consoles, which are under:
**/etc/event.d/**

What you will do is change the name to those consoles you dont want to start from tty# to tty#_something

Also you can remove privileges from users so they can't do any admin tasks, the menus will dissapear for set user

---

