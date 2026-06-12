---
title: "X Window System spontaneously restarting (without Ctrl+Alt+Backspace)"
date: 2009-03-13
forum: General Help
---

### Post by opus_az on 2009-03-13
Hi...

We have an Ubuntu 8.10 that apparently has its X Window System spontaneously restarting. The symptoms the users describe match exactly what happens with a Ctrl+Alt+Backspace but they swear they're not doing that key combo, and that it happens spontaneously while they're entering info into web page search fields.

Any ideas what may be causing this?

I may do this 'fix' [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/disableCtrlAltBackspace.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/disableCtrlAltBackspace.html) to prevent the key combo from restarting the X server.

And we'll probably just reinstall Ubuntu just to be sure. It's one of our first Linux installs in the company so who knows what kind of mischief we got into. :) It's a station used exclusively for browsing. There's a barcode scanner attached to it but we have other stations with Ubuntu and same scanners that don't have this issue. Users are not in sudoers.

So, just curious. Any ideas what might cause it?

TIA,
O.

---

### Post by Peter09 on 2009-03-13
CTRL-ALT-BACKSPACE normally closes the x server. It may be that the xserver is crashing, perhaps a faulty graphics card? Try looking in the logs,

System->Admin->System Log

for any appropriate messages.

---

### Post by daanvbaal on 2009-03-13
Have you tried to disable the desktop effects? Maybe one of the effects isn't supported by the graphics card?

---

### Post by opus_az on 2009-03-13
Hmmm. Vid card or effects sounds interesting. Maybe we flubbed the driver or something. I'll look at those logs or disable effects later today or tomorrow, it's a few miles away.

Thanks! Appreciate it.

PS: Is it X11 or X Server or X Window System? I'm seeing a mishmash of all the names.

---

### Post by daanvbaal on 2009-03-13
The X Window System is the system used for a graphical interface. One of its components is the X Server. Other programs connect to the X Server to tell it what they want to display on the screen. X11 is version 11 of this program.

---

### Post by opus_az on 2009-03-13
> **daanvbaal said:**
> The X Window System is the system used for a graphical interface. One of its components is the X Server. Other programs connect to the X Server to tell it what they want to display on the screen. X11 is version 11 of this program.

Very nice. Thanks!

---

