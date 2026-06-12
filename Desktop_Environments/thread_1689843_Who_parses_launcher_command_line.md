---
title: "Who parses launcher command line?"
date: 2011-02-17
forum: Desktop Environments
---

### Post by deleyd on 2011-02-17
What happens when I double-click a launcher on the desktop?

I want to know if I conceptually understand this correctly:
[LIST=1]
[*]I have a launcher on the desktop
[*]The desktop is GNOME
[*]I can right-click on the launcher to set it up. There I can edit the command line.
[/LIST]
When I double-click on the launcher icon, does GNOME send the command line to the bash shell? Or does GNOME parse the command line itself and call execve itself?

I'm guessing GNOME sends the command line to the shell, and the shell then parses the command line. I'd like to see some definitive documentation stating this is indeed the case, or documentation explaining how I'm mistaken and explaining what really happens.


[If I understand correctly, the desktop could also be KDE, or XFCE; and the shell could be something other than bash.]

---

