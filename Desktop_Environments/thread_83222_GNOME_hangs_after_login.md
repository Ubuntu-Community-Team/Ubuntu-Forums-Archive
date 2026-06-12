---
title: "GNOME hangs after login"
date: 2005-10-28
forum: Desktop Environments
---

### Post by f-h on 2005-10-28
Hello, i've installed Ubuntu few days ago and it was (usually) fine, until today. Gnome desktop hangs itself almost everytime after I enter my login and password (an orange rectangle which shows icons don't appear, but the screen turns brown and mouse cursor is active). Strangely, sometimes I can login (1/5 logins?) and then i have another problem: gnome applications like gnome-terminal or gconf-editor show their windows' borders, but don't redraw the content and don't respond to clicking/typing (xterm is working fine, and other gtk+ apps seems too).

What can cause the problem? Any help will be appreciated.

---

### Post by ultima2k on 2005-10-28
You probably need to install nvidia drivers, look at this:
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by f-h on 2005-10-28
I don't have nvidia chipset and i sometimes manage to log in and it was working fine until today, so the drivers probably are not an issue.

---

### Post by jvictor on 2005-11-03
Try hiding your current .gnome files. I mean all your gnome config files in YOUR HOME dir, that may force gnome to create new copies of them and that MAY solve your prob

---

