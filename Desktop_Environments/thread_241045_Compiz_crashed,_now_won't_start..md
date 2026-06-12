---
title: "Compiz crashed, now won't start."
date: 2006-08-21
forum: Desktop Environments
---

### Post by DAaaMan64 on 2006-08-21
All jump right to it, here is the error when I try to start compiz:

```

compiz.real: Another window manager is already running on screen: 0
compiz.real: No managable screens found on display :1.0
Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.


```

I installed Compiz/XGL with automatixbleeder aswell as my nvidia driver.

I was just using it and it crashed again, I search for this error and mostly got only similar ones with no solutions tied to them.  Any input is appriciated.=D>

---

### Post by BitTorrentBuddha on 2006-08-21
Try: ```
cgwd && compiz --replace gconf &
```

---

### Post by DAaaMan64 on 2006-08-21
I am sorry, I forgot to mention that I use KDE.  However here is what I tried, and the result of what I tried:

```

**daaaman64@govinda:~$** cgwd && compiz --replace gconf &
[1] 5736
**daaaman64@govinda:~$** Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.
[B]
daaaman64@govinda:~$[/B] cgwd && compiz --replace kwin &
[2] 5740
**daaaman64@govinda:~$** cgwd: Screen 0 on display ":1.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.

[2]+  Exit 1                  cgwd && compiz --replace kwin
**daaaman64@govinda:~$**


[B]
daaaman64@govinda:~$[/B] cgwd --replace kwin && compiz --replace &
[3] 5769
**daaaman64@govinda:~$** Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.
compiz.real: Another window manager is already running on screen: 0
compiz.real: No managable screens found on display :1.0



```

It didn't work obviously...  Do you have any other suggestions?  Thank you.

---

### Post by DAaaMan64 on 2006-08-22
Alright so I ran my usual "toggle-compiz-nvidia" command with sudo today may have gotten a more descriptive answer back:

```



Password:
compiz.real: Another window manager is already running on screen: 0
compiz.real: No managable screens found on display :1.0
daaaman64@govinda:~$ cgwd: Connection Error (No reply within specified time)
5952: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4628.
This is normally a bug in some application using the D-BUS library.
5952: arguments to dbus_connection_set_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4592.
This is normally a bug in some application using the D-BUS library.

** ERROR **: Not enough memory to set up DBusConnection for use with GLib
aborting...



```

Does anyone have any ideas yet?

---

