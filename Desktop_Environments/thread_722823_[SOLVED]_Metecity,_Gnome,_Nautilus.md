---
title: "[SOLVED] Metecity, Gnome, Nautilus"
date: 2008-03-12
forum: Desktop Environments
---

### Post by tad1073 on 2008-03-12
I lost the gnome desktop. Twice.

after using fluxbox and having up for a while then switching back to gnome session 

gnome is broken. Metacity won't load title bars nautilus stops running etc.


I followed a thread and it seems that deleting .gnome, gnome2 and after restarting 

x solves the problem, which it did the first time.

I swichted sessions to fluxbox, had that up for a couple of hours and 

when i  switch back to gnome the same thing happened as before. tried metacity --

replace but when I close the terminal I loose it, nautilus is not starting other than 

typing nautilus in a terminal. 

i am stuck and need some help.

---

### Post by tad1073 on 2008-03-12
problem partially resolved

---

### Post by tad1073 on 2008-03-13
What can i do to correct this.

```
:~$ gnome-settings-daemon start

** (gnome-settings-daemon:13188): WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-VJ9qP1DTGT: Connection refused

(gnome-settings-daemon:13188): GnomeKbdIndicator-WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-VJ9qP1DTGT: Connection refused

(gnome-settings-daemon:13188): GnomeKbdIndicator-WARNING **: Not connected to dbus, will not register the object
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192

** (gnome-screensaver:13208): WARNING **: failed to register with the message bus

```

---

### Post by tad1073 on 2008-03-14
bump...

---

### Post by tad1073 on 2008-03-14
How do I get my gnome desktop back? After running fluxbox I am unable to login under gnome session, metacity doen't load, nautilus doesn't load, gnome-volume-manager doesn't load. I can't open sessions manager etc...

When I do try to login to gnome session the slash screen shows Window Manger but nothing else.

---

### Post by Nzer24 on 2008-03-14
I don't really know what the problem is, but it seems like dbus is giving you errors. Dbus is how GNOME generally communicates with itself, so if it doesn't work, I'm assuming GNOME won't either. I don't know if you can reinstall it, but you can try. It might be something in the config files. Just try looking around in /etc for it.

---

### Post by tad1073 on 2008-03-14
I found a work around for my problem, which is, from fluxbox delete .gnome, .gnome2 and .gnome2_private, then ctrl+alt+backspace to logout.

From GDM, select session(gnome) enter username and password.

Since titlebars don't show I do sudo metacity --replace to start metacity.

It is a pain but it works. I think it may have something to do with sessions manager but I am no sure.

Any input will be helpful.

---

### Post by shifty2 on 2008-03-15
I got a similar error whilst using Icewm and trying to start "gnome-settings-daemon":
```
** (gnome-settings-daemon:13188): WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-VJ9qP1DTGT: Connection refused
```
I noticed that my ".dbus" folder in my home directory has root permissions, so changed it to normal access and everything worked. Not sure if that was a clever or sensible thing to do and I may have caused all sorts of chaos - but it worked for me.

---

### Post by tad1073 on 2008-03-18
Seriously, I need some major help with this problem:mad:](*,)

[SIZE="6"]HELP!!![/SIZE]

---

### Post by tad1073 on 2008-03-18
bump...

---

### Post by denver on 2008-04-17
Thank you shifty2! That solved it for me :D

---

