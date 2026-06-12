---
title: "Issues installing Project Looking Glass"
date: 2009-03-12
forum: Desktop Environments
---

### Post by Tsurugi13 on 2009-03-12
I've been messing around with multiple desktop environments recently, and I'd like to try out Project Looking Glass. Only problem is it won't install right. Using the megabundle install instructions [Here]("https://lg3d.dev.java.net/lg3d-getting-started.html#Installation"), It installs most of the way, then gives me a bunch of errors about not being able to find Xorg, and when I try to switch sessions to use it, it claims it wasn't built with X11 support and logs out. Help? :(

EDIT: Tried again, this time it worked until I tried to add it as a GDM session, then I got this:
> ./../usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
./../usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
./../usr/share/lg3d/bin/postinstall: line 43: cd: ./../usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory


EDIT AGAIN: Never mind. Managed to get it working in a window and it's kinda lame.

---

