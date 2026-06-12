---
title: "Custom Launcher altered by firefox?"
date: 2011-03-29
forum: Desktop Environments
---

### Post by jcoles on 2011-03-29
I have Gnome panel launchers for my separate installations of Firefox 3 and Firefox 4. After using Firefox 4, both launchers become Firefox 4 launchers. After using Firefox 3, both launchers become Firefox 3 launchers. Both the Name and Command fields are altered. The change occurs after log out / log in from Gnome. 

IMHO, neither the OS nor firefox should tamper with a user setting such as a launcher in a panel. 

Does anyone know more precisely what is going on here?

---

### Post by Copper Bezel on 2011-03-29
The system's environment variable for the command "firefox" can only apply to one or the other. You'd need the launcher to point directly to the appropriate binary if you want to specify.

Edit: Depending on how you have them installed, I *assume* this is what's going on. On my machine, they're different commands - firefox and firefox4.0 - because the only FF4 I have installed is the Minefield version.

---

### Post by jcoles on 2011-03-29
[QUOTE=Copper Bezel;10613879]The system's environment variable for the command "firefox" can only apply to one or the other. You'd need the launcher to point directly to the appropriate binary if you want to specify.

The Firefox 4 launcher points directly at the custom install's firefox startup script file. The Firefox 3 launcher just points to "firefox", so it relies on the path to find the app.

I'll try making the Firefox 3 launcher more specific too. Could also try pointing to "firefox-bin" instead of "firefox" which is a script that might make unwanted changes. I have run two versions of firefox before without problems.

Thanks.

---

### Post by Krytarik on 2011-03-29
I believe the reason for that is the way gnome-panel creates the desktop-files for launchers and the handling of those. When you create a custom launcher, the resulting desktop-file will get named according to the name of the specified executable. If it's both "firefox", gnome-panel may or may not get confused.

I had exact the same issue when I installed FF4 alongside FF3 a while ago. After I created a system-wide launcher for it in "/usr/share/applications", and created the panel launcher from the launcher now included by the "Applications" menu, the issue was fixed.

However, when I now try to reproduce that behaviour at my system, it doesn't work, meaning it works like you would normally expect.

So, you could either do it the way I described, or rename their desktop-files in "~/.gnome2/panel2.d/default/launchers" and assign the new file names to the existing launchers via gconf-editor, modify the key "launcher_location" therefore:
```
gconf-editor /apps/panel/objects
```Greetings.

---

