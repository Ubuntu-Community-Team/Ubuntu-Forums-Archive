---
title: "Gnome session does not save application after upgrade to maverick"
date: 2011-01-14
forum: Desktop Environments
---

### Post by lucaotta on 2011-01-14
Hi all,
after the upgrade to maverick, gnome-session-save doesn't save applications on shutdown or logout as it did on Lucid.

I've noticed the following things:

[LIST]
[*]On Lucid, if I had a stopped job in a shell, the system refused to logout or shutdown, showing a confirmation window. On Maverick, the CPU goes to 100% and then the computer shuts down; on reboot, no application is saved
[*]On Maverick, if there are NO stopped jobs in a shell, I can logout cleanly but only a few applications are saved (eg. terminal, firefox) but others aren't (eg. empathy, evolution).
[/LIST]
I've checked "Automatically remember application on exit" in "Session management" menu.

I've searched a bit on the net and the forums for "session save" problems, but it seems that I'm the only one with this problem.
Has anyone some hints to solve it? Is it a known bug?

---

### Post by radek_42 on 2011-03-25
Hi,

It seems I have the same problem. I do not restart often since I use suspend most of the time, but when I do the session is not saved. I tried 
gnome-session-save
with no luck. I was hoping to to use cron and save my session every 5 minutes or so ... 

I poked around a bit looking for directory where gnome store saved session. I found
~/.config/autostart/
~/.config/gnome-session/saved-session/
~/.config/session-state/

The first one seems to contain all autostart item (even disabled ones).

The second one contains longalphanumericalstrings.desktop files, but they do not change when gnome-session-save is used.

The third one contains gnome-terminal.desktop and nautilus.desktop. Again, they do not change when gnome-session-save is used.

I did not really investigate this issue much further than this since it's not really pressing issue, but it sure is annoying.

I would really appreciate if someone has a proper explanantion why/how this works.

Thanks,
R>

---

### Post by lucaotta on 2011-04-03
Hi,
I cannot find any reference right now, but I've found out that this feature was ditched recently because it was hard to maintain and not really well integrated into all programs (read OO.org, firefox).

The suggested way to preserve application status is to hibernate.
I hope this helps.

---

### Post by ixtos on 2011-07-13
Hi,

someone could help me on this in the German ubuntu-forum.de:

The command
```
dbus-send --session --dest=org.gnome.SessionManager /org/gnome/SessionManager org.gnome.SessionManager.SaveSession
```will correctly update the folder ~/.config/gnome-session/saved-session

I combined this command with
```
dbus-send --dest=org.gnome.SessionManager /org/gnome/SessionManager org.gnome.SessionManager.RequestShutdown
```to make my own shutdown button in the gnome panel.

I also installed wmctrl and made another short script called at startup containing
```
wmctrl -r Firefox -t 2
```to restore my firefox window always to the third desktop (counting starts at "0").

Cheers,
Hella

**EDIT:**
Just in case someone wonders: I already had this problem in Lucid. "Saving currently running applications" did the job when pressing it every time before logout, but "Automatically remember running applications when logging out" did not the same (e.g., did not update ~/.config/gnome-session/saved-session) and lost some info (e.g., konsole tab titles). I kept the checkmark on "Automatically remember..." BTW.
Hope this solution is still viable in Maverick etc.

---

