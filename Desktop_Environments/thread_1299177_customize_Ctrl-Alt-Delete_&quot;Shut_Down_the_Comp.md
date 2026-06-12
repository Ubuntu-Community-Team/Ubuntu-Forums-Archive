---
title: "customize Ctrl-Alt-Delete &quot;Shut Down the Computer&quot; options"
date: 2009-10-23
forum: Desktop Environments
---

### Post by boondocks on 2009-10-23
When you hold down Ctrl-Alt-Delete on the Gnome desktop, it brings up "Shut Down the Computer" with the options:
[LIST=1]
[*]Shut Down
[*]Restart
[*]Suspend
[*]Hibernate
[*]and a 60 second default countdown to Shut Down, if you don't select any one of the above 4 options.
[/LIST]
How can I customize this "Shut Down the Computer" with just 2 options:
[LIST=1]
[*]Shut Down
[*]Restart
[/LIST]

---

### Post by kanikilu on 2009-10-23
This, as well as being able (or rather, not able) to customize the automatic timer (60 seconds) has been brought up before, and someone please correct me if I'm wrong, but I don't think it can be done, at least not easily (without modifying source).

I think you can use polkit-gnome-authorization to set who can and can't do things like shutdown and restart, but I don't think you can edit what shows up on the GUI menu...

---

