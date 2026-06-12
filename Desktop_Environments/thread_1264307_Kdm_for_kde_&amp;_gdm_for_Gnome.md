---
title: "Kdm for kde &amp; gdm for Gnome"
date: 2009-09-12
forum: Desktop Environments
---

### Post by praveesh on 2009-09-12
I have both kde and Gnome installed and the default display manager is kdm . But the fast user switch applet of Gnome does not work under kdm. I would like to keep the login screen of kdm. Is it possible to automatically switch to gdm when I enter a Gnome session and switch back to kdm when I log out?. I think it is the only solution. Any more suggestion ? . When I searched in google, I got the way to change the default display manager, but didn't get a way to switch to gdm automatically in the Gnome .Thanks

---

### Post by purgatori on 2009-09-12
You could try creating a script such as:

```

#!/bin/bash

echo "usr/sbin/gdm" > /ect/X11/default-display-manager


```... and another such as:

```

#!/bin/bash

echo "usr/bin/kdm" > /ect/X11/default-display-manager
```Save each script, copy to /usr/bin and make executable with chmod +x. Set one to autostart in Gnome, and the other one in KDE.

In theory, it would be possible to create a much more sophisticated script which could check whether Gnome or KDE is running via /etc/init.d/./gnome-session status or something, and then modify the default-display-manager file accordingly, but this is quite beyond my current knowledge.

---

### Post by praveesh on 2009-09-12
> **purgatori said:**
> You could try creating a script such as:

```

#!/bin/bash

echo "usr/sbin/gdm" > /ect/X11/default-display-manager


```... and another such as:

```

#!/bin/bash

echo "usr/bin/kdm" > /ect/X11/default-display-manager
```Save each script, copy to /usr/bin and make executable with chmod +x. Set one to autostart in Gnome, and the other one in KDE.

In theory, it would be possible to create a much more sophisticated script which could check whether Gnome or KDE is running via /etc/init.d/./gnome-session status or something, and then modify the default-display-manager file accordingly, but this is quite beyond my current knowledge.

thanks . I shall try. But I didn't understand "make executable with chmod +x". Can you please explain it?

---

### Post by jacksaff on 2009-09-12
If you don't understand what chmod is then you absolutely, definitely do not want to be mucking around with your log-in manager! You could very easily leave yourself in a situation where you can't log-in graphically and if you don't have a fair bit of terminal knowledge you're going to be pulling some hair...
Only one log-in manager is supposed to be running at any one time. You either get the pretty screen of kdm or the feature you want of gdm.

---

### Post by tubasoldier on 2009-09-12
GDM should be the way for you to go then.
DO not muck about with your login manager. The KDE user switching seems to be more understanding that Gnome's fast user switch applet. It does well with KDM or GDM.

---

### Post by praveesh on 2009-09-13
Thanks for everyone's advice. I will study bash scripting more

---

