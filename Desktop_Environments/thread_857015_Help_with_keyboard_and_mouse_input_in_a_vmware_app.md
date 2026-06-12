---
title: "Help with keyboard and mouse input in a vmware appliance"
date: 2008-07-12
forum: Desktop Environments
---

### Post by sal02452 on 2008-07-12
On Windows Vista, I'm running VMWare Player with an ubuntu804desktop appliance.  It works great, except for one annoyance with the keyboard input and one annoyance with the mouse input.

Keyboard input: It treats the quote and apostrophe keys as special "do something based on the next keystroke" keys rather than as a simple quote and apostrophe.  This happens in gnome applications and in plain ol' xterm.  In the "Language Support" window, "Enable support to enter complex characters" is not checked (and it never has been).  Any idea how I can turn off this feature-or-bug?

Mouse input: The mouse scroll wheel doesn't work.  So I edited xorg.conf and added "Options Protocol imps/2", which made the scroll wheel start working, but it kind of broke the X server.  It messed up the virtual appliance window size and resizability, and it broke the mouse movement into and out of the virtual appliance, and it made the onscreen pointer flakey.  So I removed the "imps/2" line.  Is there a good way to turn on scroll wheel support?

Thanks much.
Sal

---

### Post by orzechowskid on 2008-08-06
I had these exact same problems as well.  Did you get your appliance from the VMWare site too?

You'll need to edit /etc/X11/xorg.conf in a couple of places.  To fix the keyboard issue, remove or comment out the line containing the "XkbVariant" option in the "Generic Keyboard" InputDevice section.  To fix the mouse scroll wheel issue, add this new line to the "Configured Mouse" InputDevice section:

Option "ZAxisMapping" "4 5"

Save the file, restart your X server, and you should be good to go.

---

### Post by sal02452 on 2008-08-08
Both of those answers worked great.  Thanks much!

Sal

---

