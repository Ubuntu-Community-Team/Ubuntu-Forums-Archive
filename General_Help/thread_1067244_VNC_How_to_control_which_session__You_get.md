---
title: "VNC: How to control which session  You get?"
date: 2009-02-11
forum: General Help
---

### Post by philatnhs on 2009-02-11
Pardon me if this is the wrong Forum, but I did not see one that seemed more relevant.

I am fairly new to Linux, very new to Ubuntu.  We have a machine which is controlled by a Ubuntu box, and it has VNC installed on it.

When I call in, using either Chicken of the VNC or real VNC, it drops me into a seperate session.

Problem is, my main use is to remotely help the user, which means we need to be looking at the same session, same desktop.

I am not even sure which version is running on this box.  Any pointers would be greatly appreciated.

Thanx
Phil

---

### Post by geirha on 2009-02-11
There should be a vnc server installed by default that does just that. You go to System -> Preferences -> Remote Desktop to enable and configure it.

---

### Post by philatnhs on 2009-02-18
OK, I found it, although it was a little deeper then that.  I do not see any settings which would control the behavior of coming up with a new session vs the actual desktop, and I am not sure of this is a version of VNC or not.

Is this something other then VNC?  I am fine with that as long as I can access that desktop from both Windows machines and Macs.

---

### Post by geirha on 2009-02-18
The built/default vnc server is called vino. If the other vnc server is a different one, I'm guessing they'll fight for the port. Try giving one of the servers a different port than 5900, then connect using the appropriate port.

---

