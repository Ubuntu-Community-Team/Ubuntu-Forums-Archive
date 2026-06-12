---
title: "Cannot open main menu in LXDE, Ubuntu 14.04"
date: 2014-06-19
forum: Desktop Environments
---

### Post by buisteric on 2014-06-19
Hi,

I just tried to install LXDE and just have no way to open up the main menu. I searched on Google for hours and found things about ALT-F1 (not working), Windows (not working), Alt-space (not working). Seems that LXDE is not configured properly in Ubuntu 14.04 and ALT-F1 opens the menu by default. Why isn't there any keyboard shortcut to open the menu? How am I supposed to use the system if I cannot reach any application? I am just stuck and will have to kill the session: oh, no CTRL-Alt-Baskspace, that key was removed as well a while ago. So I will have to log on a console and kill X.org from there. I am at a dead end, because my HTPC configuration relies on Linux and Unity became too slow over time. Now it requires ten to fifteen seconds to open up the main menu, even though the machine has 4Gb of RAM (and cannot have more due to motherboard limitation). All other Linux distributions come with GNOME3 which as well as no obvious way to reach main menu or KDE which is even heavier on system resources. Other lightweight desktop managers such as Xfce lack keyboard shortcuts as well.

Thanks for any help.

---

### Post by sudodus on 2014-06-19
To run another desktop environment, LXDE instead on Unity, you must select it at the log in screen. Click on the round symbol and select the desktop you want to use. See the attached picture.

---

### Post by buisteric on 2014-06-19
Finally got it working. I had to edit ~/.config/openbox/lxde-rc.xml and add the following in the <keyboard> section:

  <keybind key="Super_L">
      <action name="Execute">
        <command>lxpanelctl menu</command>
      </action>
  </keybind>

After restarting the session, the Windows key now opens the start menu.

---

