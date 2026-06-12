---
title: "Found fix for NX keyboard mapping problem"
date: 2008-12-20
forum: General Help
---

### Post by astrashe on 2008-12-20
When I installed 8.10 on my client machines, I had a glitch with remote access using NX -- some keyboard mappings weren't set up properly.

This page at No Machines has the answer:

[http://www.nomachine.com/tr/view.php?id=TR11F02131](http://www.nomachine.com/tr/view.php?id=TR11F02131)

Apparently it's a problem with version 1.5 of the X Org server.  On the client side, add the following lines to /etc/X11/xorg.conf:

Section "ServerFlags"
    Option "AutoAddDevices" "false"
EndSection

If you don't have a US keyboard, be sure to go to the page linked above, as you need to do more to prevent the fix from dropping you into a US keymap.

(I hope it's OK to post this here.  I wanted the info to show up in a search of the forums, but I wasn't sure where to put it.)

---

### Post by tohecz on 2009-12-25
This help made my local X lose contact with keyboard, so I didn't even manage to log in, or to switch to non-X console. (I could use the onscreen keyboard, but still wasn't able to get back all the changes; linux LiveCD saved me.) TAKE THIS AS A WARNING!!!

---

