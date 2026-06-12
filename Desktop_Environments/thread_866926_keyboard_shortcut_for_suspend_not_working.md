---
title: "keyboard shortcut for suspend not working"
date: 2008-07-22
forum: Desktop Environments
---

### Post by martin6 on 2008-07-22
Hi,

The keyboard shortcut for suspend not working. 

I tried "System/Preferences/Keyboard shortcuts", and used "ctrl+alt+s", but it does not seem to work (nothing happened).

The other function like "logout" works, I can customize to use the shortcut.

Any suggestions will be greatly appreciated.

Thanks

Martin

---

### Post by pauper on 2008-07-24
Post the output:

```
cat /sys/power/state
```

Are you able to suspend it from System--Quit or via command:

```
echo -n "mem" | sudo tee /sys/power/state
```

See [http://www.mjmwired.net/kernel/Documentation/power/states.txt](http://www.mjmwired.net/kernel/Documentation/power/states.txt)

---

### Post by jamesrl on 2008-08-25
For me suspend works completely fine from the command line, but the keyboard shortcut for suspend as set in "System > Preferences > Keyboard Shortcuts", does absolutely nothing.  Others seem to have the same problem.

I am trying to create either a keyboard shortcut that when run goes straight to suspend.  The best I can do at the moment is bind a key combo to "Log Out" (say <Control><Alt>O and then press <Alt>-P (for suspend from the logout menu).

I tried quickly searching for where the shortcuts are stored in gconf-editor and couldn't find them, and also did an extremely quick search for where the source code for the "keyboard shortcuts" is, and also couldn't find it.  Does anyone know where this stuff is stored?  Or how suspend from the log-out menu circumvents needing a password?
 
I know its straightforward to create a custom keyboard shortcut to say 
```
gksudo /etc/acpi/sleep.sh force
```
using gconf-editor in the metacity section but that then requires a password (not necessarily ideal, if you want to say just very quickly put your computer to sleep before leaving/going to bed).  [Sure if i stored my password to a plain-text file I could likely get around this, but then my password would be in a plain text file (incredibly insecure).]

---

### Post by jamesrl on 2008-08-25
Ok, so I did more snooping and solved the problem, by a backend routine.

Basically, go to gconf-editor -> /apps/Metacity/keybinding_commands
and add to an unused command (say command_9):
```
dbus-send --session --dest=org.freedesktop.PowerManagement --type=method_call /org/freedesktop/PowerManagement org.freedesktop.PowerManagement.Suspend
```
Then go to global keybindings run_command_9, and set your particular keystroke (e.g., I used <Control><Alt>Z (zzz's for sleep)).

And you are done, got a keyboard shortcut to suspend.

If this doesn't work for you, you might ask how I got here (or if you are trying to do something slightly similar).   From this post I found how to search for source-code by just greping through /usr/bin and using apt-get source: [http://ubuntuforums.org/showpost.php?p=1722420&postcount=2]("http://ubuntuforums.org/showpost.php?p=1722420&postcount=2")
and from there I found the source and saw that it was sending commands via the dbus.  Then a google search gave these two posts:
[http://lists.freedesktop.org/archives/dbus/2006-July/005079.html]("http://lists.freedesktop.org/archives/dbus/2006-July/005079.html") and 
[http://lists.freedesktop.org/archives/dbus/2006-July/005078.html]("http://lists.freedesktop.org/archives/dbus/2006-July/005078.html")

where I figured out that the `dbus-send` command given above that sent suspend to my desktop when I click on the suspend button.  Specifically as the command given in 2006 referenced something slightly different, I'll show how I found my version.  I opened up python and typed:
```

import dbus
bus = dbus.SessionBus()
bus.list_names()

```
Saw org.freedesktop.PowerManagement in there, so opened the object
```

object = bus.get_object('org.freedesktop.PowerManagement', "/org/freedesktop/PowerManagement") 
print object.Introspect(dbus_interface="org.freedesktop.DBus.Introspectable")

```
and then saw a method named Suspend in there.
So then I could come up with the dbus-send command given above at the top.

---

