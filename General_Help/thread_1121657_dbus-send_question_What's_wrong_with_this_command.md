---
title: "dbus-send question: What's wrong with this command?"
date: 2009-04-10
forum: General Help
---

### Post by Cheesehead on 2009-04-10
I'm teaching myself how to use DBus. The following python program works great to create a test notification on Xubuntu 8.04...but the shell command to do exactly the same thing using exactly the same DBus method doesn't work. **What am I doing wrong with the shell command?**

(Yeah, I know there are other ways to do this. The point is that I want to master the dbus-send command)
```

# THIS ONE WORKS
#!/usr/bin/env python
"""This is a python 2.5 script that creates a notification using dbus."""
import dbus
item = ('org.freedesktop.Notifications')
path = ('/org/freedesktop/Notifications')
interface = ('org.freedesktop.Notifications')

icon = ''
array = ''
hint = ''
time = 10000   # Use seconds x 1000
app_name = ('Test Application')
title = ('NOTIFICATION TEST')
body = ('This is a test of the notification system via DBus.')

bus = dbus.SessionBus()
notif = bus.get_object(item, path)
notify = dbus.Interface(notif, interface)
notify.Notify(app_name, 0, icon, title, body, array, hint, time)

```
```

# THIS ONE FAILS
dbus-send --session --dest=org.freedesktop.Notifications \
--type=method_call --reply-timeout=10000 /org/freedesktop/Notifications \
org.freedesktop.Notifications.Notify string:'Test Application' uint32:0 \
string: string:'NOTIFICATION TEST' \
string:'This is a test of the notification system via DBus.' \
array:string: dict:string: int32:10000
```

---

### Post by parvulos on 2009-10-10
Hi Cheesehead, 

you used empty containers, but dbus-send manpage says:

```

D-Bus  supports more types than these, but dbus-send currently does not.
Also, dbus-send does not permit empty containers or nested containers 
(e.g. arrays of variants).

```parvulos

---

### Post by www.rzr.online.fr on 2009-12-04
> **parvulos said:**
> Hi Cheesehead, 

you used empty containers,


Same with 0 length strings, can this API be used w/ dbus-send ?


```

dbus-send --session --type=method_call --reply-timeout=10000 \
  --dest=org.freedesktop.Notifications \
  /org/freedesktop/Notifications  org.freedesktop.Notifications.Notify \
  string:"app_name" \
  uint32:0 \
  string:'app_icon' \
  string:"summary" \
  string:"body" \
  array:string:"" \
  dict:string:string:"",""\
  int32:10000

```

---

### Post by karsti on 2009-12-13
Hello!

I like your script in the first post very much.

Only that it doesn't solve my problem, which is to have a script that doesn't run in user context (i.e. started by anacron) send messages to my screen.

Do you happen to know if it's possible to include the --system parameter an if that has the desired effect?

Thanks in advance, Karsten

---

