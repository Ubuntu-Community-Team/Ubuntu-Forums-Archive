---
title: "xfce4-session doesn't load xfce4-session.rc in .config"
date: 2009-04-30
forum: Desktop Environments
---

### Post by PacSci on 2009-04-30
To get Xfce to start up Compiz when I run it, I copied the xfce4-session.rc from /etc/xdg/xfce4-session/xfce4-session.rc to ~/.config/xfce4-session/xfce4-session.rc, modified the command count and changed the commands to look like:

```
[General]
SessionName=Default
SaveOnExit=False
DisableTcp=True

[Failsafe Session]
Count=5
Client0_Command=compiz
Client0_PerScreen=False
Client1_Command=python /home/me/bin/logit
Client1_PerScreen=False
Client2_Command=xfce4-panel
Client2_PerScreen=False
Client3_Command=Thunar,--daemon
Client3_PerScreen=False
Client4_Command=xfdesktop
Client4_PerScreen=False

```

The "/home/me/bin/logit" is a script I wrote to log if the session is getting read or not. It's not. Does anyone know why xfce4-session isn't reading my session, and how to get it to do so? (The original session file is still in /etc/xdg/xfce4-session, by the way. I didn't want to change the system default.)

---

### Post by sashoalm on 2010-10-04
Hello, did you manage to get this working?

---

