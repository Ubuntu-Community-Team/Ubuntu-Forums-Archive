---
title: "Unity still visible after GNOME install"
date: 2011-11-02
forum: Desktop Environments
---

### Post by cnickl on 2011-11-02
I recently switched from Unity to GNOME 3.  The problem is that after logging in with GNOME shell, it seems like the Unity title-bar is still visible.  All of the menu items are messed up (unreadable). All windows displayed are fine however. I attached a screenshot.  I did a Google search but nothing I found seems to describe my problem.

Any help is appreciated.

Chris

---

### Post by Pirate Zoro on 2011-11-02
install gnome tweak tool ```
sudo apt-get install gnome-tweak-tool
``` Find it under the name "Advanced Settings" in the menu. Click the desktop tag, and turn off the option to have the file manager control the desktop. You won't have icons on the desktop, but the global menu will no longer appear behind the panel.

---

### Post by markbl on 2011-11-03
There is no need to turn off your Desktop. Just type the following command in a terminal:
```

echo '[ "$DESKTOP_SESSION" != "ubuntu" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy

```

Then log out/in.

That won't affect Unity at all but will stop the Unity global menu stuff affecting gnome-shell.

---

### Post by wildjiji on 2011-11-03
This is [Bug 826771]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/826771").

And, Nautilus (1:3.2.1-0ubuntu2) has been released to solve this issue.

What you have to do is just to update by following command.

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by markbl on 2011-11-03
That command I quote above fixes other "unity global menu" bugs that affect gnome-shell though, so it is still worth doing. E.g. try turning off the menu on the top of gnome-terminal without that fix (this bug still occurs on ubuntu 11.10 updated to today).

---

### Post by wildjiji on 2011-11-03
[QUOTE=markbl]That command I quote above fixes other "unity global menu" bugs that  affect gnome-shell though, so it is still worth doing. E.g. try turning  off the menu on the top of gnome-terminal without that fix (this bug  still occurs on ubuntu 11.10 updated to today).     [/QUOTE]

I filed [Bug #826771]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/826771") with following screenshot.

[https://launchpadlibrarian.net/77304758/gnome-shell-oneiric-001.jpg](https://launchpadlibrarian.net/77304758/gnome-shell-oneiric-001.jpg)

Only by installing Nautilus (1:3.2.1-0ubuntu2),  unity global menu("File", "Edit" and so on, above screenshot is Japanese, e.g. "Edit"="&#32232;&#38598;") under the gnome-shell panel is **disappear**ed in gnome-session, and the Nautilus does not affect Unity in ubuntu-session.
Of course, I don't use the workaround that you and [Bug #874943  ]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/874943")describe. 

Therefore, I can turn off the menu (unity global menu) on the top of gnome-shell without your workaround.

But you are not fixed... I misunderstand this problem?...

---

### Post by cnickl on 2011-11-03
Thanks guys for the quick responses. Unfortunately none of the suggestions worked.

In fact it's actually worse.  I'm not sure if that was there before, but whenever I open a window, or move the mouse to the edge of the screen the entire display "jitters" in addition to my problem described before.  Graphics Card problem maybe?

---

### Post by nogdog21 on 2012-01-06
The suggestion posted by MarkBL fixed this issue for me.  Thanks!

-Drew

---

