---
title: "Auto Logoff [GNOME]"
date: 2008-10-22
forum: Desktop Environments
---

### Post by Abdul Haqq on 2008-10-22
I know this question has been asked before but no satisfactory answers given that I can find.

Problem: Small domestic situation. Users run off leaving their session open. Need to get the session to close automatically after x minutes of idle time and back to the login screen.

Thanks

---

### Post by kilroy423 on 2008-10-23
You could go to System>Preferences>Screensaver and check Lock screen when screensaver is active

---

### Post by Abdul Haqq on 2008-10-23
I do not want to lock the screen. There has been much discussion on this in various forums to date no one has an answer.

What I want is say after 30mins of idle time the user will be logged out and X restarted. Nice if open work is saved but not essential. This is much like Windows behaves.

---

### Post by cyfur01 on 2008-10-24
One possible hack is to create a psuedo-screensaver that will do the logout action. It's not perfect, but the following will automatically log me out of my session.

1. Create a script to do the logout:
```

cd /usr/lib/xscreensaver
sudo touch logout
sudo chmod +x logout
sudo gedit logout

```
Paste:```

#! /bin/bash
# Mimics the normal logout command
gnome-session-save --kill --silent

```

2. Add this to the gnome-screensaver list:
```

cd /usr/share/applications/screensavers
sudo gedit logout.desktop

```

Paste:```

[Desktop Entry]
Encoding=UTF-8
Name=LogOut
Comment=Logs out the user
TryExec=antinspect
Exec=logout
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver

```
As you can see, I copied this from the antinspect screensaver... works as is, though you could clean up the TryExec line probably.

3. Set this as the screensaver like you normally would, and wait for it to take effect.


Note:
Found one flaw with this... every time I go to change it from the usual GUI menu, it just logs me out :P 
You'll have to edit the preferences from the gconf-editor program, or switch the logout script to non-executable (chmod -x /usr/lib/xscreensavers/logout) before going to change the preferences and set it back to executable afterwards.

---

### Post by rhiensch on 2011-03-06
Check timeoutd.
Flexible user timeout daemon timeoutd enforces the time restrictions specified in /etc/timeouts. When invoked in daemon mode (without any parameters) timeoutd backgrounds itself, then scans /var/run/utmp every minute and checks /etc/timeouts for an entry which matches that user, based on: - The current day and time" - The tty that the user is currently logged in on" - The user's login ID" - Any primary or secondary groups the user is in" Written by Shane Alderton (shane@ion.apana.org.au)

---

### Post by amrypma on 2011-11-30
timeoutd is not an option.
It either kills every user after the idle timeout or it doesn't do anything.

X runs on its own tty with which you don't interact. result your session gets killed at the idle timeout.

---

