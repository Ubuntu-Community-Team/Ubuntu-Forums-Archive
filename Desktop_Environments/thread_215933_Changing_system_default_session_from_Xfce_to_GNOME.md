---
title: "Changing system default session from Xfce to GNOME"
date: 2006-07-14
forum: Desktop Environments
---

### Post by mssever on 2006-07-14
How do I change the default system session (the login default) back to GNOME after I installed xubuntu-desktop? I know I can set it per-user, but I want to fix the system-wide setting.

---

### Post by jayemef on 2006-07-14
When at the login screen, click on the **Options** button. You should see something about a session. Select Gnome and log in as usual. You should be prompted as to whether to make Gnome your new default. Choose yes.


EDIT: disregard -- misunderstood the question...

---

### Post by aysiu on 2006-07-14
I don't think there *is* a system default. I think it's definitely on a per user basis.

---

### Post by mssever on 2006-07-15
There is a default somewhere. Try this: create a new user and log on. What session do they use? On my system, it defaults to Xfce.

Of course, it's a relatively simple matter to change the default on a per-user basis, but that' not what I'm looking for.

---

### Post by aysiu on 2006-07-15
Some of this output from *grep -inr session /etc* might interest you: ```
/etc/xdg/xubuntu/gdm/gdm.conf:30:# any user session started by GDM to exit immediately while USR1 behaves like
/etc/xdg/xubuntu/gdm/gdm.conf:105:# Note that a post login script is run before a PreSession script.  It is run
/etc/xdg/xubuntu/gdm/gdm.conf:109:PreSessionScriptDir=/etc/gdm/PreSession/
/etc/xdg/xubuntu/gdm/gdm.conf:110:PostSessionScriptDir=/etc/gdm/PostSession/
/etc/xdg/xubuntu/gdm/gdm.conf:128:# session, but it shares a lot of stuff with that.  See the provided default
/etc/xdg/xubuntu/gdm/gdm.conf:130:BaseXsession=/etc/gdm/Xsession
/etc/xdg/xubuntu/gdm/gdm.conf:131:# This is a directory where .desktop files describing the sessions live.  It is
/etc/xdg/xubuntu/gdm/gdm.conf:133:# with KDM.  Note that <sysconfdir>/dm/Sessions is there for backwards
/etc/xdg/xubuntu/gdm/gdm.conf:135:SessionDesktopDir=/etc/X11/sessions/:/etc/dm/Sessions/:/usr/share/gdm/BuiltInSessions/:/usr/share/xsessions/
/etc/xdg/xubuntu/gdm/gdm.conf:136:# This is the default .desktop session.  One of the ones in SessionDesktopDir
/etc/xdg/xubuntu/gdm/gdm.conf:137:DefaultSession=xfce4.desktop
/etc/xdg/xubuntu/gdm/gdm.conf:168:# Should a second login always resume the current session and switch VT's on
/etc/xdg/xubuntu/gdm/gdm.conf:170:#AlwaysLoginCurrentSession=true
/etc/xdg/xubuntu/gdm/gdm.conf:225:# affects truly local sessions.
/etc/xdg/xubuntu/gdm/gdm.conf:258:# Maximum open XDMCP sessions at any point in time.
/etc/xdg/xubuntu/gdm/gdm.conf:259:#MaxSessions=16
/etc/xdg/xubuntu/gdm/gdm.conf:266:# some time and wouldn't allow another session.
/etc/xdg/xubuntu/gdm/gdm.conf:268:# The number of seconds after which a non-responsive session is logged off.
/etc/xdg/xubuntu/gdm/gdm.conf:406:# XDMCP session should only get a color, this is the sanest setting since you
/etc/xdg/xubuntu/gdm/gdm.conf:417:# Show the Failsafe sessions.  These are much MUCH nicer (focus for xterm for
/etc/xdg/xubuntu/gdm/gdm.conf:420:#ShowGnomeFailsafeSession=true
/etc/xdg/xubuntu/gdm/gdm.conf:421:#ShowXtermFailsafeSession=true
/etc/xdg/xubuntu/gdm/gdm.conf:422:# Normally there is a session type called 'Last' that is shown which refers to
/etc/xdg/xubuntu/gdm/gdm.conf:423:# the last session the user used.  If off, we will be in 'switchdesk' mode
/etc/xdg/xubuntu/gdm/gdm.conf:424:# where the session saving stuff is disabled in GDM
/etc/xdg/xubuntu/gdm/gdm.conf:425:#ShowLastSession=true
/etc/xdg/xubuntu/gdm/gdm.conf:477:# The chooser is what's displayed when a user wants an indirect XDMCP session
```

---

### Post by mssever on 2006-07-17
I've already hunted through gdm.conf to no avail. :( Thanks anyway.

---

