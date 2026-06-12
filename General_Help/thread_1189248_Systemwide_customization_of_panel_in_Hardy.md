---
title: "Systemwide customization of panel in Hardy?"
date: 2009-06-16
forum: General Help
---

### Post by darthchaosofrspw on 2009-06-16
I want to make some systemwide customizations to the panel without having to log in to other user accounts. In other words, I want the following changes to be the default configuration for any new users I may add in the future.

Here's what I want.

[LIST]
[*]Just one panel on the bottom, set to a pixel size of 24, fixed position, full width, and situated on the bottom left.
[*]I want to have the Application applet without the Applications text beside the icon.
[*]I want to remove the Help launcher beside the Firefox launcher and add a Thunderbird launcher, Pidgin launcher, and set the Trash applet and Show Desktop applet to the right of the Pidgin launcher.
[*]I want to put the Task List applet beside the Show Desktop applet.
[*]I want the Separator or Spacing applet to the right of the Task List applet and set to "expand".
[*]I want the xfce4-mixer applet to the right of the Separator or Spacing applet.
[*]I want the System Tray applet to the right of the xfce4-mixer applet.
[*]I want the Clock applet to the right of the System Tray applet set to 12 hour mode and displaying AM/PM.
[*]I want the Panel Actions applet to the right of the Clock applet with action type set to Quit.
[/LIST]

Any help would be greatly appreciated.

EDIT: SOLVED!

I deleted all the files located in /etc/xdg/xfce4/panel, customized my taskbars the way I wanted them, copied all files from /home/user/.config/xfce4/panel, and then pasted those files in /etc/xdg/xfce4/panel. Created a new user, logged out, logged in to the new user account, and voila, the setting are just the way I wanted them!

---

