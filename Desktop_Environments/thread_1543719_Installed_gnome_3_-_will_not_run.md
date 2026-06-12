---
title: "Installed gnome 3 - will not run"
date: 2010-08-01
forum: Desktop Environments
---

### Post by xircon on 2010-08-01
I run gnome-shell --replace and I get:

```
 gnome-shell --replace
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  157 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15
Failed to start shell
Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 278, in <module>
    shell = start_shell()
  File "/usr/bin/gnome-shell", line 135, in start_shell
    (server_glx_extensions, client_glx_extensions, glx_extensions) = _get_glx_extensions()
  File "/usr/bin/gnome-shell", line 73, in _get_glx_extensions
    server_glx_extensions = set(re.split("\s*,\s*", glxinfo_map['server glx extensions'].strip()))
KeyError: 'server glx extensions'
steve@n5010:~$ Cannot register the panel shell: there is already one running.
/usr/bin/compiz (core) - Fatal: glXCreateContext failed
/usr/bin/compiz (core) - Error: Failed to manage screen: 0
/usr/bin/compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

```

Any ideas?

---

### Post by KdotJ on 2010-08-01
Maybe try do an update, what manager are you usin now? Compiz?

---

### Post by xircon on 2010-08-01
Yes Compiz is installed, the compositing in KDE4.5 is badly broken so I was using it.  Have uninstalled and now get:

```
gnome-shell --replace
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  157 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  18
  Current serial number in output stream:  18
Failed to start shell
Traceback (most recent call last):
  File "/usr/bin/gnome-shell", line 278, in <module>
    shell = start_shell()
  File "/usr/bin/gnome-shell", line 135, in start_shell
    (server_glx_extensions, client_glx_extensions, glx_extensions) = _get_glx_extensions()
  File "/usr/bin/gnome-shell", line 73, in _get_glx_extensions
    server_glx_extensions = set(re.split("\s*,\s*", glxinfo_map['server glx extensions'].strip()))
KeyError: 'server glx extensions'
steve@n5010:~$ Cannot register the panel shell: there is already one running.
Window manager warning: Failed to read saved session file /home/steve/.config/metacity/sessions/104740967069979b3d12806952755575200000016660000.ms: Failed to open file '/home/steve/.config/metacity/sessions/104740967069979b3d12806952755575200000016660000.ms': No such file or directory
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

```

---

### Post by xircon on 2010-08-03
I think this is an ATI Radeon problem, just tried Sauerbraten and get:
```
 ./sauerbraten_unix 
Using home directory: /home/steve/.sauerbraten
init: sdl
init: net
init: game
init: video: mode
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  157 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  19
  Current serial number in output stream:  19

```

Which is very very similar!

---

