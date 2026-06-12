---
title: "mandatory settings"
date: 2012-07-13
forum: Desktop Environments
---

### Post by N-t-F on 2012-07-13
Hello everyone. :)

I'm trying to lock some settings in order to run "kiosk" systems with Ubuntu 12.04, and it's getting me mad.

The main purpose is to prevent screen locking, hibernation and user-switching. Being able to restore usual shortcuts (Ctrl-Alt-Backspace to kill the X session, mostly) and make them mandatory for all users would be great too.

I've tried to do that both with xfce (after installing xubuntu-desktop) and Gnome Classic.

**XFCE:**

I've tried to use the settings editor to change shortcuts, but the "locked" checkbox doesn't seem to be checkable, even when the editor is launched with gksudo. So I have edited:
```
nano /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
```
to get something like:
```
<property name="&lt;Primary&gt;&lt;Alt&gt;Delete" type=string" unlocked="rootlocal" value="xfce4-session-logout"/>
```
The result is that the property is indeed locked for normal users, but still set to xflock4. I have yet to find the entries for hibernation and others, but if this one already doesn't work properly...
I have found a nice workaround for screen-locking, though:
```
chown rootlocal.admins /usr/bin/xflock4
chmod 770 /usr/bin/xflock4
```
That way, only admins can lock the system. Xfce doesn't seem to offer user-switching, which is perfect as far as I'm concerned.

So, I'm left with the issues of hibernation and suspend. There is also the Ctrl-Alt-Backspace shortcut.


**Gnome-classic:**

I've tried just what I did before (Ubuntu 10.04): setting mandatory options through gconf-editor. It still appears to write them properly in:
```
/etc/gconf/gconf.xml.mandatory/%gconf-tree.xml
```
Unfortunately, this does not seem to have any impact on users, who can still lock things, freeze things, and otherwise wreak havoc as they see fit.
I've not tried to set mandatory shortcuts with gnome-classic yet, but I've tried to do it through Unity's GUI some time ago, and it did not seem to work.

I would be very grateful if anyone here could hint me in the right direction, because I admit I'm about to bang my head over the wall (and possibly naughty users, too :p).

---

### Post by Krytarik on 2012-07-13
> **N-t-F said:**
> **Gnome-classic:**

I've tried just what I did before (Ubuntu 10.04): setting mandatory options through gconf-editor. It still appears to write them properly in:
```
/etc/gconf/gconf.xml.mandatory/%gconf-tree.xml
```Unfortunately, this does not seem to have any impact on users, who can still lock things, freeze things, and otherwise wreak havoc as they see fit.
I've not tried to set mandatory shortcuts with gnome-classic yet, but I've tried to do it through Unity's GUI some time ago, and it did not seem to work.
Since Oneiric 11.10, a lot of Gnome and Ubuntu session-related settings have started to be stored in DConf, migrating from GConf. The post by *mc4man* here pretty much reflects the current state of my knowledge as well:

[http://ubuntuforums.org/showthread.php?p=12097266#post12097266](http://ubuntuforums.org/showthread.php?p=12097266#post12097266)

Regards.

---

### Post by N-t-F on 2012-07-16
Thank you for the answer! :)

There's not much improvement, unfortunately, and I have lost another day at work with this issue.

Regarding xfce, I admit I don't understand how settings work (or even if they work). And my workaround only prevents screen-locking through keyboard shortcut or GUI. When the system goes to sleep, then a password is asked to access the session again. *sigh*

Regarding Gnome-classic, I have tried to follow your hint, which led me to the gsettings command. I'm not sure if it applies to Gnome-classic, Gnome 3 or Unity, or all of them, though. The use of:
```
gsettings list-recursively
```
apparently didn't show any key capable of preventing user-switching or screen-locking. Does anyone know if such keys exist or how to find them ?

As a side note, I haven't found a way to restore the usual Ctrl-Alt-Backspace to kill X. There is an option in Unity to do that (under settings -> keyboard -> options), but it doesn't seem to work, even as a single "simple" user (that is without taking into account mandatory settings).

[rant] All in all, it is very frustrating and time consuming to have to cope with the same problems, version after version, just because painfully discovered working solutions get broken along the way. ](*,)[/rant]

I'll open other threads more specifically devoted to each point.

---

