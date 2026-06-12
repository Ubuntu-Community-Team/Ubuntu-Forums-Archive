---
title: "Gnome 3.32 configuration questions"
date: 2019-08-02
forum: Desktop Environments
---

### Post by dictum99 on 2019-08-02
Gnome 3.32 is what comes with 19.04.

Is there an option to save the desktop configuration and have it come up exactly as I left it upon reboot? I open all these xterms, etc.and want them reopened upon login.

Second, does 3.32 support virtual desktops? I want to have multiple desktops and navigate between them with a defined keystroke.

---

### Post by dictum99 on 2019-08-02
Gnome 3.32/Ubuntu 19.04

 Is there an option to save the desktop configuration and have it come up exactly as I left it upon reboot? I open all these xterms, etc.and want them reopened upon login.

 And  3.32 support virtual desktops? I want to have multiple desktops and navigate between them with a defined keystroke.

Third, I want point to raise window behavior instead of click to raise.

---

### Post by coffeecat on 2019-08-02
Thread merged and moved to ***Desktop Environments***.

Please do not cross-post duplicates in different parts of the forum. This causes confusion and dilutes community effort.

---

### Post by deadflowr on 2019-08-02
As far as I know saving desktop sessions is broken in Gnome.

Gnome uses workspaces (much like virtual desktops)
See: [https://help.gnome.org/users/gnome-help/stable/shell-workspaces.html.en]("https://help.gnome.org/users/gnome-help/stable/shell-workspaces.html.en")

While the default setup for workspaces is dynamic you can set it to static if you want.
Install gnome tweaks (or just search Software for Tweaks) and open it go down to workspaces and check the option for static workspaces; 
then toggle how many you ant in the number of workspaces counter.

Tweaks also has window focus option set in the Windows section.

---

### Post by Dennis N on 2019-08-02
Save Session:
Try: d[B]conf-editor > org > gnome > gnome-session > auto-save-session
[/B]
Yes there are virtual desktops: 
[https://help.gnome.org/users/gnome-help/stable/shell-workspaces-switch.html.en](https://help.gnome.org/users/gnome-help/stable/shell-workspaces-switch.html.en)

Switchers:
I use  gnome-shell-extensions "Alternatetab", "Workspace indicator" and "All Windows" as workspace and window switchers.

---

### Post by dictum99 on 2019-08-03
[HTML][/HTML]> **Dennis N said:**
> Save Session:
Try: d[B]conf-editor > org > gnome > gnome-session > auto-save-session
[/B]
Yes there are virtual desktops: 
[https://help.gnome.org/users/gnome-help/stable/shell-workspaces-switch.html.en](https://help.gnome.org/users/gnome-help/stable/shell-workspaces-switch.html.en)

Switchers:
I use  gnome-shell-extensions "Alternatetab", "Workspace indicator" and "All Windows" as workspace and window switchers.

Thank you. I will try these.

---

