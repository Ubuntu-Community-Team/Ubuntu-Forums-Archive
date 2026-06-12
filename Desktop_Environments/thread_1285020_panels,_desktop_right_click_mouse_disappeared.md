---
title: "panels, desktop right click mouse disappeared"
date: 2009-10-07
forum: Desktop Environments
---

### Post by tarekmg on 2009-10-07
I installed ubuntu 9.04 on Acer Aspire 3500 laptop with SIS video card. It was working fine since I installed it. Yesterday when I started the laptop, the desktop does not show any menu or icons and the mouse right click menu is not not shown. The computer become useless.
Before that installation and to try ubuntu I had installed as a guest on a desktop with XP SP3 as a host using Sun VirtaulBox 3.0.6. Again yesterday the same happened to that virtual PC. All ubuntu menus, panels and icons disappeared.

Is there any other way to overcome this than clean installation. and If I did clean installation, what should I do to prevent this from happening again.

Thanks in advance,

---

### Post by Brandon Williams on 2009-10-07
Can you think of anything specific reconfiguration activities that you might have carried out? For example, did you try out the UNR desktop switcher?

If nothing comes to mind, try checking the value of /desktop/gnome/session/required_components_list using gconf-editor. Does it say ["windowmanager","panel","filemanager"]?

---

### Post by tarekmg on 2009-10-08
[SIZE=2]I think on both ubuntu installations (laptop and desktop VM) the packages update manager was operating. I did not install ny thing new or change any configuration.
I cannot do the check you require because I do not have nay control on the screen. The screen appear empty of all the icons, menu, panels. just the background. Also the mouse right click menu is not there.
However, ctrl + alt + F2 is working and I tried several things but nothing working.[/SIZE]

---

### Post by Brandon Williams on 2009-10-08
If you have ctrl+alt+F2, then you can start gconf-editor. 

That said, if you don't have the panel, then I'm confused by the fact that ctrl+alt+F2 is working. Are you running gnome? If you are, then the panel must be running somewhere if you can get the run dialog to pop up. Maybe you've got more than one app trying to control the desktop.

Try running gnome-system-monitor to see what processes are running. Look for gnome-panel, nautilus, and metacity (or compiz). Which of these are running?

---

### Post by mullenrbock on 2009-10-08
I had that problem a few weeks ago, and I just reinstalled. I turn my laptop on a few minutes ago, and the same exact thing happened. I'm running fluxbox now, but this is really annoying. 

> 
Try running gnome-system-monitor to see what processes are running. Look for gnome-panel, nautilus, and metacity (or compiz). Which of these are running?

The problem with that is, if there are no panels or context menus, you can't do that.

EDIT:
I ran gnome-panel from an xterm in Fluxbox, and the panels show up fine. So something isn't starting gnome-panel when I log in...

---

### Post by Brandon Williams on 2009-10-08
> **mullenrbock said:**
> The problem with that is, if there are no panels or context menus, you can't do that.

You're right, I just wasn't thinking. cltrl+alt+F2 != alt+F2.

Forget about gnome-system-monitor, you can do it from a console login with:
```
ps -fU $USER | less
```

You can see what's in the required_components_list from the command line with:
```
gconftool-2 --get /desktop/gnome/session/required_components_list
```

And you can get an xterm window to show from the console with:
```
DISPLAY=:0 xterm
```

---

### Post by mullenrbock on 2009-10-09
Has anyone discovered a fix for this yet? Anyone else having this problem?

---

### Post by tarekmg on 2009-10-12
since this problem happened and I tired several things. Things mentioned in this thread, things mentioned elsewhere in the internet, and lastly things that I invented myself.

NO SUCCESS.

I did a clean installation hoping it will not happened again.

---

