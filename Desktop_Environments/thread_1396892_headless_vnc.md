---
title: "headless vnc?"
date: 2010-02-02
forum: Desktop Environments
---

### Post by dld on 2010-02-02
Some time ago I ran x11vnc on a headless Ubuntu machine and vncviewer on my main machine.  Both are now running 9.10 updated as much as possible.  Running x11vnc on headless and vncviewer, vinagre, ssvnc, or tsvnc on main
gives an xterm running on an empty ubuntu background--no taskbars or trays
or icons.  I can start up metacity with the xterm and get its contributions.
I can run synaptic, etc.   But I can't get the Ubuntu bars, and hence can't
do things like System->Preferences->...

Any ideas or help?   Don

---

### Post by adam814 on 2010-02-02
While logged into the remote system try typing this in the xterm, then restarting X and connecting again:
```
echo "exec gnome-session" > ~/.xinitrc
```

---

### Post by dld on 2010-02-02
A .xinitrc file is created in my home directory on the headless  machine.  Incidently, I run x11vnc on that machine as root via the following:

alias vnc='x11vnc -auth /var/lib/gdm/:0.Xauth -display :0 -noxfixes'

---

