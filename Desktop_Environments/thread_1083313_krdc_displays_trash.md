---
title: "krdc displays trash"
date: 2009-02-28
forum: Desktop Environments
---

### Post by beckejc on 2009-02-28
I am running Intrepid Kubuntu KDE 4 on an amd64 machine.  I have a xubuntu machine (32 bit) that I have set up with the vino vnc server.

Problem is this:  When I connect to my vino server on the xubuntu machine via krdc on the Kubuntu machine, I see a trashed and barely intelligible facsimile of the actual display showing on the Xubuntu machine.

The colors are all mangled and the display of any letters on the machine are blurred beyond recognition.  The cursor doesn't track to the display correctly.

I tried configuring the color depth and the resolution on both machines but to no avail.  I am ready to chuck the whole idea.

Anybody else seen this remote-desktop-screen-from-hell?

---

### Post by tarlton on 2009-03-15
I have the same problem. Using Intrepid 32bit on the server machine, and Jaunty alpha 5 on the viewer machine. Appears to be a problem with the server, as Krdc works perfectly accessing windows machines running UltraVNC servers.

Update: I found a work-around here [http://forum.kde.org/kde4-looks-awful-over-vnc-t-16651.html](http://forum.kde.org/kde4-looks-awful-over-vnc-t-16651.html)
not pretty, but if you absolutely need krfb to work.

---

