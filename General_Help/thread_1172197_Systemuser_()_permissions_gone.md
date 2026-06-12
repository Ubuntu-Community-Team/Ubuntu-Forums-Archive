---
title: "System/user (?) permissions gone"
date: 2009-05-28
forum: General Help
---

### Post by gingaz on 2009-05-28
Hello,

i'm pretty sure such question was already asked, but i can't find correct keywords for it.

Here's the problem:

after week of working everything was OK, then after reboot sound and network drivers could not be loaded. Errors:

when i try to run network manager mannualy:
ginga@gingatron:~$ nm-applet --sm-disable
:

** (nm-applet:5607): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service.
  Message: 'Connection ":1.106" is not allowed to own the service "org.freedesktop.NetworkManagerUserSettings" due to security policies in the configuration file'

BUT with sudo it works.


When i try to test device in System>Pref>Sound it alerts me
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused"

I even cannot enter "Users and groups" application:
"You are not allowed to access the system configuration."


Any ideas what to do?

Thank you! :)

---

### Post by nothingspecial on 2009-05-28
Try ```
users-admin
```
or if that doesn`t work
```
sudo users-admin
``` to enter the users and groups gui.

No idea if it will work, just an idea.

---

### Post by gingaz on 2009-05-28
Nop, didn't help:
No protocol specified

(users-admin:8471): Gtk-WARNING **: cannot open display: :0.0


Damn, everything that was controled by system is without permission now :(

---

### Post by gingaz on 2009-05-29
Is there any logs of executed commands in terminal? Something i have did, but i can't remember - what.

Or maybe it's possible to restore permission settings to default?

---

