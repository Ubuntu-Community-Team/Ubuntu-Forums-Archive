---
title: "Aero Snap Like Windows 7"
date: 2010-06-11
forum: Desktop Environments
---

### Post by Dumbestcrayon on 2010-06-11
I like the Aero snap that Windows 7 has a lot and I found this great article on one of my favorite websites.

[http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html](http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html)

Everything is there except for the command to restore the window. I set Maximize [command 0] to <Super>Up Arrow, etc like it is in Windows.

Does anybody know the command to use that I could put in Command 3 to assign to <Super>Down Arrow to restore the window or Unmaximize as some people call it?

eg. wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz is for maximize window which I have assigned to <Super>Up Arrow


EDIT: Nevermind, I read the manual for a little while and learned how to use wmctrl which is what I wanted to do in the first place.

Here is what I came up with.

wmctrl -r :ACTIVE: -b toggle,maximized_vert,maximized_horz

---

