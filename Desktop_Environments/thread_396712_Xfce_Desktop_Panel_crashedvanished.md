---
title: "Xfce Desktop Panel crashed/vanished"
date: 2007-03-29
forum: Desktop Environments
---

### Post by Jc1991 on 2007-03-29
I'm running Xubuntu 6.10 with Xfce 4.3.99.1.

The desktop panel (and only the panel) has vanished and does not come back with a restart of the Xserver or of the computer itself. Right and middle clicks work and bring up the correct menu as always. The panel vanished while I was checking my email last night, so I was not making any major changes to my system at the time.

Running xfce4-panel via the command line brings the panel back, although I'm not sure of the normal options appended to this command on startup, or how to get it to run on startup.
Thanks ahead of time for any help.

---

### Post by kellemes on 2007-04-01
delete your ~/.cache/sessions/xfce_don't_know_how_there_called_sessionfiles.

---

### Post by Jc1991 on 2007-04-02
That worked, thanks!

---

