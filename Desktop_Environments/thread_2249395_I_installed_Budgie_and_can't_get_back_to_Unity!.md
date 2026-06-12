---
title: "I installed Budgie and can't get back to Unity!"
date: 2014-10-21
forum: Desktop Environments
---

### Post by johnnybrown on 2014-10-21
I'm new to the forums and fairly new to Ubuntu. I was looking for a lightweight alternative to Unity. After seeing half of an OMG!Ubuntu article on Budgie, I decided to give it a try. Well, it didn't go well at all. In fact, my computer is unusable. I have the standard Unity desktop background with no buttons and no taskbar. There is no way to launch a terminal or log out. If I right click my mouse, I only have 4 options with zero help: New Folder, Paste, Organize desktop by name, and Keep Aligned. I've tried ctrl-alt-t and nothing happens. I've tried ESC and nothing happens. I've tried ctrl-alt-delete and nothing happens. At this point, I just want out of this completely useless desktop environment and go back to Unity. Can someone help me log out????

---

### Post by grahammechanical on 2014-10-21
[http://www.omgubuntu.co.uk/2014/07/install-budgie-evolve-os-desktop-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/07/install-budgie-evolve-os-desktop-ubuntu-14-04)I have no idea what budgie is, except that it is small exotic bird, but did you remove Unity or Ubuntu desktop? Usually when we install an alternative desktop we still keep the previous desktop and we select either the new or the old desktop session at the login screen.

I have installed Gnome Session Flashback and now at the login screen I click the Ubuntu icon to the top right of the password panel and I can select Ubuntu, (that is Unity), Gnome Flashback (Compiz) or Gnome Flashback (Metacity). Can you not do the same and select between Budgie and Ubuntu?

By the way, when I right click the desktop background wallpaper I get not only the 4 options you mention but I also get New Document and Change Desktop Background, clicking which will get us to System Settings. That won't help you.

Not knowing the detail of what you did it is not wise to offer advice as it might make things worse. Except re-install. Sounds drastic and it is drastic but it does work.

Have you tried Ctrl+Alt+F2? If that gets you to a Linux console log in and run

```
dconf reset -f /org/compiz/
setsid unity
unity --reset-icons
```

To get back to the desktop  use Ctrl+Alt+F7

If you want to shut down or reboot and you are at a Linux console then to reboot run 

```
sudo shutdown -r now
```

and to shut down run

```
sudo shutdown -h now
```

Regards

EDIT: I have just read this

[http://www.omgubuntu.co.uk/2014/07/install-budgie-evolve-os-desktop-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/07/install-budgie-evolve-os-desktop-ubuntu-14-04)

I know what you mean when you said that you half read it. This is the half that you did not read.

> [COLOR=#4F4F4F][FONT=Lato]Budgie is not stable, finished nor is it officially supported on Ubuntu. It is in active development and features remain missing, including, but not limited to: no network management support, no volume control applet (keyboard keys will work fine), no notification system and no way to &#8216;pin&#8217; apps to the task bar.[/FONT][/COLOR]
[COLOR=#4F4F4F][FONT=Lato]It also doesn&#8217;t play too nicely with Ubuntu&#8217;s overlay scrollbars, some GTK themes, and session management (e.g., logout, restart, etc.) on distributions using Upstart (like Ubuntu, [though that&#8217;s changing]("http://www.omgubuntu.co.uk/2014/02/ubuntu-debian-switching-systemd")) does not work.[/FONT][/COLOR]


No comment.

---

### Post by CantankRus on 2014-10-21
click the menu at bottom left then type in "terminal".
Open a terminal and run
```
kill -9 -1
```
This will log you out where you can pick the session by clicking the icon as shown in pic.

You can also open a terminal by creating a new folder and then navigating to **/usr/share/applications**
and locating the terminal launcher.

---

