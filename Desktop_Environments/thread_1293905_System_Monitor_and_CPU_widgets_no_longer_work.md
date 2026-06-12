---
title: "System Monitor and CPU widgets no longer work"
date: 2009-10-17
forum: Desktop Environments
---

### Post by kvarley on 2009-10-17
I ran some updates and while configuring samba-common the update-manager froze. I came back a while later and killed the update-manager window.

Now when I go to add a system monitor or a CPU scaling widget to the panel it gives me this:

> [CENTER]The panel encountered a problem while loading "OAFIID:GNOME_MultiLoadApplet".

Do you want to delete the applet from your configuration?[/CENTER]

Any ideas? Thanks

---

### Post by ajgreeny on 2009-10-17
In a terminal use the command ```
sudo dpkg --configure -a
``` and it might put right the non configuration that occurred when your system froze.

---

### Post by louieb on 2009-10-17
Don't have fix. But a workaround. When I get that message I just log out then login again and everything starts up normally.  I Guess its some sort of timing issue.

---

### Post by kvarley on 2009-10-18
Solved. It was a much bigger problem.

Somehow when the update broke it left me with an error with the desktop environment.

So in terminal I re-installed the environment. Then installed "ubuntu-desktop", that fixed it, for now...

Thanks for the help anyway!

---

