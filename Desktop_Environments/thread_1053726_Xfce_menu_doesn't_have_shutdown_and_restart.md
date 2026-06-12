---
title: "Xfce menu doesn't have shutdown and restart"
date: 2009-01-28
forum: Desktop Environments
---

### Post by Tomás Ó hÉilidhe on 2009-01-28
When I want to restart my computer or shut it down, I have to go to "Quit" in the Xfce menu. This brings me to the login screen where I have to click "Shutdown".

Is there anyway of getting shutdown and restart shortcuts directly in the Xfce menu?

On other thing, is the "Quit" command supposed to be as abrupt as it is? For instance, in Windows XP, when you go to log off, it asks you if you want to save your data in the currently open programs. However in Xfce, when you click "Quit", everything just disappears instantly and you're left at the login screen. Is this by design? (I'm not saying it's a bad thing, it's just gonna take getting use to).

---

### Post by icheyne on 2009-01-29
I'm not sure if it's possible to add shutdown and restart, but this page tells you how to get to the XFCE menu editor.

[http://www.xfce.org/documentation/4.2/manuals/xfdesktop](http://www.xfce.org/documentation/4.2/manuals/xfdesktop)

---

### Post by videodrome on 2009-01-30
just add a button that runs the following command:

xfce4-session-logout

---

### Post by ravisghosh on 2009-12-10
> **videodrome said:**
> just add a button that runs the following command:

xfce4-session-logout

This command is for logout and not shutdown and restart.

The "Quit" button and "Logoff" in the application menu allows the user to just logoff, and there is no option to directly shutdown.

Also, xfce4-menueditor does not exist. I googled it and it appears that this has been removed from xfce 4.6.

Any solution to add shutdown/restart buttons?

---

### Post by ravisghosh on 2009-12-10
Just found the solution.

1. Go to Applications>Settings>>session and startup>general.
2. Check "Prompt on Logout."

Now, whenever the user clicks on Quit or Log Out, she will be asked whether she wants to shutdown, log out, restart, etc.

---

