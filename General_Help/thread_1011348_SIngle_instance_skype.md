---
title: "SIngle instance skype"
date: 2008-12-14
forum: General Help
---

### Post by KillerKiwi on 2008-12-14
This quick bit of python will show the skype window if its started else it starts a new instance..

```
#!/usr/bin/env python
import dbus
import sys
import os

try:
    # Try and set skype window to normal
    remote_bus = dbus.SessionBus()
    out_connection = remote_bus.get_object('com.Skype.API', '/com/Skype')
    out_connection.Invoke('NAME single-instance')
    out_connection.Invoke('PROTOCOL 5')
    #out_connection.Invoke('SET WINDOWSTATE MAXIMIZED')
    out_connection.Invoke('SET WINDOWSTATE NORMAL')
    out_connection.Invoke('FOCUS')
except:
    os.system("skype")
    sys.exit()
```

Note: You will need to ok the dbus call with skype the first time.. make sure to click the "Remember this selection" checkbox

---

### Post by kruykaze on 2010-12-15
Nice thanks.

---

### Post by tora201 on 2010-12-28
Or one could just go here: [http://forum.skype.com/index.php?showtopic=332401](http://forum.skype.com/index.php?showtopic=332401)

Does the same thing! (Wait a minute... IT IS THE SAME THING! Naughty, naughty? Or just coincidence?

---

### Post by caue.rego on 2011-03-08
That only creates, at best, a way to add a shortcut to Skype that won't open another instance. But I need a way to prevent Skype itself to do it because of **Deskbar**, **Docky** and **cardapio**.

It would be nice to be able to solve this! :)

---

### Post by kiaulpienius on 2011-08-12
thanks

---

### Post by jamesgthang on 2011-09-27
Thanks, this python script was helpful.  Here is a post showing some steps to use this script with the Unity Launcher in Ubuntu 11.04.

[http://ubuntuforums.org/showthread.php?t=1851256](http://ubuntuforums.org/showthread.php?t=1851256)

---

