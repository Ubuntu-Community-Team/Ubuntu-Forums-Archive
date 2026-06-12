---
title: "Gnome 3.4.1 Desktop Switching Multiple Monitors"
date: 2012-05-04
forum: Desktop Environments
---

### Post by PirateFanAZ on 2012-05-04
I have upgraded to Ubuntu 12.04 and am using the Gnome 3.4.1 shell.  I have noticed that when I switch workspaces only my primary monitor switches, applications on my second monitor remain, they don't switch to display the applications I am/would like to run on another workspace.

I have addressed this in previous verions of Ubuntu/Gnome 3 with gconf-editor.  The settings needed to make this change no longer are in gconf-editor.

I have tried using the command:

gsettings set org.gnome.shell.overrides workspaces-only-on-primary false

to change this behavior but I receive this message after executing the command:

GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.

The switching behavior of my multiple monitors does not change after executing the command.

Anyone know how to make both monitors switch desktops in Ubuntu 12.04/Gnome 3.4.1?

Thanks.

---

### Post by kiirokurisu on 2012-05-04
Have you looked in dconf-editor? This is where settings are migrating to.

---

### Post by PirateFanAZ on 2012-05-04
Thanks for the assistance kiirokurisu.

I did not have dconf-editor installed so I used the Software Center and installed it.  I ran it from a console window via sudo and migrated to org/gnome/shell/overrides and there I found a setting called workspaces-only-on-primary that was checked by default.  I unchecked it and closed out dconf-editor.

I then started dconf-editor again and migrated to the same location to verify that the setting was still unchecked.  It was.

I then logged out of Gnome and logged back in.  My secondary monitor still does not switch when I switch desktops, only my primary monitor does.  I got the same behavior after rebooting my machine.

Any other ideas?

Thanks again.

---

### Post by scorp123 on 2012-05-04
> **PirateFanAZ said:**
>  ... via sudo ...  You modified root's settings, not your own.

Just call dconf-editor ... without "sudo". That will modify *your *settings. When you're done, press Alt+F2, enter "r" (and hit the "Enter" key) ... and Gnome 3.x will restart (you can leave your applications open, they will not be harmed). The change will become active instantly and work as expected.

---

### Post by PirateFanAZ on 2012-05-04
Thank you both.

scorp123 you are dead on correct.  I tested on a VM running 12.04 and it worked like a charm.  I will apply to my home machine tonight after work.

Thanks again.

---

### Post by PirateFanAZ on 2012-05-05
Just a quick update.

Using dconf-editor to expand my desktops across both monitors worked on my VMware Player 4.0.2 virtual machine running 12.04 LTS (upgraded from 12.04 beta 1).  The same procedure did not change the behavior of my PC (HP Pavilion) running 12.04 LTS (upgraded from 11.10).

Unless anyone has another suggestion I'm going to do a fresh install of my PC and go from there.

---

### Post by PirateFanAZ on 2012-05-06
I have performed a clean install of 12.04 LTS and installed dconf-editor from the Software Center.  I ran dconf-editor and unchecked workspaces-only-on-primary located at org/gnome/shell/overrides.  I now have workspaces switching on both monitors.

---

