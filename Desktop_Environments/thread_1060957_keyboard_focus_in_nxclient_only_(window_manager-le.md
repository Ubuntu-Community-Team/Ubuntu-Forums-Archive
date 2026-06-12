---
title: "keyboard focus in nxclient only (window manager-less) session"
date: 2009-02-05
forum: Desktop Environments
---

### Post by misha680 on 2009-02-05
I have an X session that I use specifically to log onto nxclient (so I can take my desktop with me wherever I go). Here is my /usr/share/xsessions/nxclient.desktop:

```
[Desktop Entry]
Encoding=UTF-8
Name=NX
Comment=NoMachine
Exec=/usr/bin/nxclient-run
Icon=
Type=Application
```

and here is /usr/bin/nxclient-run:

```
#!/bin/sh
syndaemon -d -t
/usr/NX/bin/nxclient &
exec xterm

```

Works fine except after nxclient runs, if I just want to start it up again by running /usr/NX/bin/nxclient & in terminal, it doesn't have keyboard focus. Only way to input password is to type it in xterm, left click to copy, and middle click in nxclient to paste. Any suggestions for how I can have proper keyboard focus?

Thank you
Misha

---

