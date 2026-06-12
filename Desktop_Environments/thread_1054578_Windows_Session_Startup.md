---
title: "Windows Session Startup"
date: 2009-01-29
forum: Desktop Environments
---

### Post by Kingpong on 2009-01-29
I accidentally removed a Windows Startup from the system>preferences>sessions

Now all of my applications only open in the top left of the screen without windows.  How do I get this back?

---

### Post by x33a on 2009-01-29
if you disabled window manager from startup, just re-enable it.

---

### Post by Kingpong on 2009-01-29
I removed it.  How do I add it back?

---

### Post by x33a on 2009-01-29
press alt+f2, the type gnome-session-properties.

scroll down and check the window manager.

then restart the system.

---

### Post by Kingpong on 2009-01-29
alt - F2 does not do anything for me.

---

### Post by Kingpong on 2009-01-30
I figure it out. Since the ALt+F2 was not working for me I opened up a terminal and entered "sudo gnome-session-properties"

This showed the Windows Manager and it was checked. I copied down the settings and closed the window.

I then went back to the terminal and entered "gnome-session-properties".  This opened the same window but it did not have the Windows Manager at all.  So I added it with the information from the previous window.  

Restart and everything is working.

Thanks for the help.

---

### Post by x33a on 2009-01-30
good thing that you figured it out yourself. that's how you get better over time :D

---

### Post by Kingpong on 2009-01-30
> **x33a said:**
> good thing that you figured it out yourself. that's how you get better over time :D

I agree.  I just needed some direction of where to start.

Thanks!

---

