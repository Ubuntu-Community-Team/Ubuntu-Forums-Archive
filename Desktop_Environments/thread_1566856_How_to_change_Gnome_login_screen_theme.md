---
title: "How to change Gnome login screen theme?"
date: 2010-09-02
forum: Desktop Environments
---

### Post by Lawlerito on 2010-09-02
So, here's the story: I did some messing about with the ambiance-maverick-beta theme and it worked fine, but the login screen, missing the default Ambiance theme, defaulted to Clearlooks. **Clearlooks.** So, I tried upgrading to Maverick, thinking it would default the login screen to the new themes. No such luck. Help, please!

---

### Post by sisco311 on 2010-09-02
Add gnome-appearance-properties to GDM's autostart directory:
```
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. The appearance properties window should show up on the GDM screen. 

Configure GDM how you want, then close the window and log back in. 

When you're done and want the window to stop opening with GDM, run:

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by Lawlerito on 2010-09-02
Thank you. That worked perfectly. Changing my thread's status to solved.

*EDIT: Wow. A problem solved in under 10 minutes. This forum really *is *awesome.*

---

### Post by keildozer on 2010-09-03
that didn't help me much I want to totally transform it. Basically I want customize layout and style like some of the stuff on Gnome-Look.org .

---

### Post by Lawlerito on 2010-09-03
> **keildozer said:**
> that didn't help me much I want to totally transform it. Basically I want customize layout and style like some of the stuff on Gnome-Look.org .
You could do that in older versions.

---

### Post by keildozer on 2010-09-03
Well is there another OS similar to Ubuntu that allows that?

---

### Post by Lawlerito on 2010-09-03
> **keildozer said:**
> Well is there another OS similar to Ubuntu that allows that?
Try Debian.

---

### Post by sisco311 on 2010-09-04
> **keildozer said:**
> that didn't help me much I want to totally transform it. Basically I want customize layout and style like some of the stuff on Gnome-Look.org .
[noparse]
The new GDM (>=2.28) is not compatible with the old themes. You either wait until someone creates new GDM themes or try to create new themes yourself. 


It's not so hard, changing the GTK theme, background, mouse cursor, etc. is trivial & if you want to customize the "simple greeter", you could edit the /usr/share/gdm/gdm-greeter-login-window.ui file with GLADE.[/noparse]

---

