---
title: "Fluxbox does not start properly!"
date: 2006-07-28
forum: Desktop Environments
---

### Post by defmer on 2006-07-28
i installed fluxbox using synaptic and then restarted my sys. during login, I choose fluxbox session and logged in.

all that came up on the screen was a bar at the bottom of the screen. nuthing else works, when i do a right click it says fluxbox and thats it.

i am able to change between the sessions on the task bar. But no terminal or windows .....nuthin.

thanks for helping guys.
 defmer

---

### Post by Tomosaur on 2006-07-28
Hit ctrl+alt+f2 to bring up a terminal (ctrl+alt+f12 to get back to fluxbox). In the terminal you should be able to edit your fluxbox config, although I can't remember right now what it's called. I think it may be .fbox.conf or something similar. It's a hidden file anyway, and it will be in your /usr/home/<you> directory.

You should be able to manually add menu items fairly easily, although from what I can remember, fluxbox should come with basic menus already configured.

---

### Post by roostishaw on 2006-07-28
The config files are in /home/you/.fluxbox/ 
The menu is /home/you/.fluxbox/menu
Startup file is in /home/you/.fluxbox/startup
> (ctrl+alt+f12 to get back to fluxbox)
I think the default for the current X session is ctrl+alt+F7

---

### Post by tical2756 on 2007-02-12
When you installed fluxbox using synaptic, you only checked "fluxbox".  do a search for fluxbox in synaptic, there are about 8 other files that need to be installed.  fluxconf...

---

