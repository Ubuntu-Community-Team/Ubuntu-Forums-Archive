---
title: "VNCServer ignoring xstartup"
date: 2005-04-23
forum: Desktop Environments
---

### Post by halcy on 2005-04-23
So I have VNCServer starting upon boot, and when i connect to it i from my windows machine it puts me straight into gnome.  I have created a xstartup script in ~/.vnc/xstartup and placed in it:

```

#!/bin/bash
/usr/bin/kdm &

```

And it still starts me in gnome when i use vnc rather than kde.  When i graphically log in from the actual machine (rather than over vnc) i get the selection before logging in on whether i want my session to be gnome or kde.

Any ideas on how I can switch this to KDE as it seems to completely ignore what I have in xstartup.  (Also the script running vncserver is running it under my username).

Thanks.

---

### Post by cedjo on 2005-04-23
I had the same problem:

create a file with the name .xsession in your user home directory.
just write **startkde** in this file and save it

restart your vncserver and that's it!!!

NB: if you install xfce4 and want to use it, replace **startkde** with **startxfce4**

---

### Post by halcy on 2005-04-23
thanks a ton that worked great!  Now this may be a stupid question, but is it possible to run vncserver so that when you connect its like remote desktop in that it asks you for a username/pw then logs you into that account? or is that impossible since it fully depends on what user runs the vncserver process?

thanks!

---

