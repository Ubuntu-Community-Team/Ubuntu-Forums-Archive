---
title: "Accessinn openbox menu with a panel"
date: 2007-11-06
forum: Desktop Environments
---

### Post by fishy27 on 2007-11-06
Hi!

I've installed openbox and love it, but have a slight problem.  When I've got a window maximised, I can no longer access the menu without resizing the current window every time, because there's no "empty" desktop to right click on!  I'm getting around this at the minute by defining a small section of the screen at the top as a margin in ~/.config/openbox/rc.xml which I can click on.  Is there a better way?  If there's some way of assigning a middle click (when the cursor's anywhere, even over a window) as the menu accessing button, that'd be perfect.

Thanks in advance,
Rob.

---

### Post by urukrama on 2007-11-07
You could assign a keyboard shortcut to the menu. I always assign Alt+F1 to the menu. This is what you should have in your rc.xml file (in /home/USERNAME/.config/openbox/):

> <keybind key="A-F1">
      <action name="ShowMenu">
        <menu>root-menu</menu>
      </action>
    </keybind>

Reconfigure Openbox (in the menu 'Reconfigure') and whenever you press Alt-F1 your menu should appear.

You could also use a panel, like pypanel, and configure it such that it doesn't occupy a small portion of the screen at the bottom left, where you can click to access the menu. Using the margins is another option, as you've mentioned.

You could also use a panel that has a menu built in, such as [lxpanel]("http://sourceforge.net/project/screenshots.php?group_id=178827"), [fbpanel]("http://fbpanel.sourceforge.net/"), xfce4-panel, gnome-pane (all in the repos)l. Though these panels do not show the Openbox menu, their menus work just fine in Openbox (note that for the last two you won't be able to use the power options in pure openbox).

---

### Post by fishy27 on 2007-11-07
Thanks urukrama, the keybinding works really well :)

Cheers,
Rob.

---

