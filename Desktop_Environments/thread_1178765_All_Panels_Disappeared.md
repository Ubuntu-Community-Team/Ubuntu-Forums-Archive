---
title: "All Panels Disappeared"
date: 2009-06-04
forum: Desktop Environments
---

### Post by zhangmaster12 on 2009-06-04
All my panels disappeared. No panel on top or bottom of the desktop. 
Can't access any programs b/c no Applications panel.

Cannot access terminal either. Alt-f2 doesn't work. I tried making a desktop shortcut that executes the command sudo terminal. That doesn't work either. Because I can't access terminal, I can't reinstall dsktop or gnome-panel.

Help! Hopefully this isn't a bug.

---

### Post by gettinoriginal on 2009-06-05
I would suggest this for a start:  Good Luck
System Restore
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by Brandon Williams on 2009-06-05
> **zhangmaster12 said:**
> I tried making a desktop shortcut that executes the command sudo terminal.

Instead, try creating a shortcut that runs 'gnome-terminal' and then use sudo at a command prompt after the terminal opens.

Can you remember anything that you did recently that might have caused the panel to disappear? I can think of two possibilities off the top of my head: 1. used the netbook remix desktop-switcher; 2. deleted items from main menu. If we know what you did recently then we might be able to suggest a specific remedy.

Before trying to fix this with global-scope solutions (reinstalling packages), are you certain that it's a global problem and not an issue in the user config? Try creating a completely new user, log-in, and see whether the panels come up for that user. If they do, then it's a user-specific config issue that will be solved by deleting your .cache, .config, and .local directories.

---

### Post by m.ayad on 2009-06-05
please run the fallowing :

```
$gconftool-2 --shutdown
```

```
$rm -rf ~/.gconf/apps/panel
```

```
$pkill gnome-panel
```

---

### Post by Jonnox on 2009-06-05
If you get locked in like that, you can always hit:

Ctrl + Alt + F1 (or F2, F3...) to access another getty (basically a terminal) and you can uninstall, re-install stuff from there. Hope that helps :)

---

### Post by zhangmaster12 on 2009-06-06
Thanks guys, I did Ctrl-alt-f2 and reinstalled ubuntu-desktop. Still no help.

Did the recovery mode and tried to fix x server. Didn't work

When I try sudo apt-get install gnome panel, it tells me gnome-panel is already the latest version.

As for if I did anything recently: I switched from Netbook remix style desktop to regular desktop using the option in preferences. After the switch everthing was normal. I could see me application/places/system panel and my bottom panel. Then I turned off my pc and went to bed. Next morning, all panels are gone. 

@Brandon Williams how do I create a new user?

Btw, I need to figure this out my monday night. On monday night, if this isn't figured out, Im installing Xubuntu. (This is my mom's netbook, and shes goin away on a trip Tuesday morning. She needs the netbook.)

Edit:
OH SNAP!!
I made a shortcut that executes gnome-terminal, (before it was sudo gnome-terminal). It opened a terminal and I was able to run gnome-panel. My panel came back!!! But! theres a catch. Ill paste the debug message in a bit

Edit2 Heres the debug/error message:

qin@qin-laptop:~$ gnome-panel
** (gnome-panel:3681): DEBUG: Adding applet 0.
** (gnome-panel:3681): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:3681): DEBUG: Adding applet 1.
** (gnome-panel:3681): DEBUG: Adding applet 2.
** (gnome-panel:3681): DEBUG: Adding applet 3.

(gnome-panel:3681): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 24
** (gnome-panel:3681): DEBUG: Adding applet 4.
** (gnome-panel:3681): DEBUG: Adding applet 5.
** (gnome-panel:3681): DEBUG: Adding applet 6.
** (gnome-panel:3681): DEBUG: Adding applet 7.
** (gnome-panel:3681): DEBUG: Adding applet 8.
** (gnome-panel:3681): DEBUG: Adding applet 9.
** (gnome-panel:3681): DEBUG: Adding applet 10.
** (gnome-panel:3681): DEBUG: Adding applet 11.

(gnome-panel:3681): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:3681): DEBUG: Adding applet 12.

After the message, there is a blinking cursor. The process doesn't end however and if I stop it by doing something like pressing ctrl-c, my panels disappear.

Now, when I open a window, there is a panel missing. Also, the bottom panel is there, but doesnt work.
This is difficult to say with words so Ill take a sreenshot.

[IMG]http://i129.photobucket.com/albums/p225/zhangmaster12/screen1.png[/IMG]
[IMG]http://i129.photobucket.com/albums/p225/zhangmaster12/screen2.png[/IMG]

For the firefox window, I cannot move or resize it.I can however, close a normal file explorer window.

This is how the desktop looks without running gnome-panel
[IMG]http://i129.photobucket.com/albums/p225/zhangmaster12/screen3.png[/IMG]

---

### Post by Brandon Williams on 2009-06-07
> **zhangmaster12 said:**
> As for if I did anything recently: I switched from Netbook remix style desktop to regular desktop using the option in preferences. After the switch everthing was normal. I could see me application/places/system panel and my bottom panel. Then I turned off my pc and went to bed. Next morning, all panels are gone.

The 'Known Jaunty Jackalope Bugs' thread and the 'Release Notes' are both very good places to look before posting a question. This problem and the solution/work-around are described in both places. Read [the bug report](https://bugs.launchpad.net/desktop-switcher/+bug/349519) to find an explanation of how to fix the immediate problem, as well as an updated package from the developer that should be installed.

---

### Post by UbuntuNerd on 2009-06-07
can you please try this command in a terminal Im almost sure it will work:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

