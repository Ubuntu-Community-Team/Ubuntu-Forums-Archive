---
title: "A few questions to Gnome 3"
date: 2013-08-16
forum: Desktop Environments
---

### Post by rotation2 on 2013-08-16
I have to switch to Gnome 3 and there are a few questions:

1) Are there close buttons when a window is maximized? 
I have seen none

2)
Is only the current open window shown in the program list in the task bar on top?
Is there another way to switch between programs as alt-tab and clicking on activities?

3)
clicking on activities is a little slow. I am running (testing) ubuntugnome in a Virtual machine right now.
Is there a way to speed the opening of activities up?



5)
How do I organize the order of favourite icons?

6)
How do I create own desktop Shortcuts, e.g drag firefox from activities to desktop?

7)
How do I switch to desktop quickly? is there a keyboard shortcut?

8)
Is the keyboard shortcut ctrl-alt-t to open a terminal working everywhere?
In every open program?

9)
Is there a way to add shortcuts to the taskbar (right of Activities left of open-window-list)?

10)
How do I enable themes?
what is the difference between shell theme and current theme?
for shell theme I have to install user-theme extension. I read a few articles about it. It appears to be in quite a bunch of repos, is there an official repo for it?

11)
How do I open a program using alt-f2 and root privileges?
gksudo, sudo gksu is not working.

Thanks

---

### Post by Jonor on 2013-08-16
(1) There seems to be a bug on maximized nautilus graphical directory windows on my box such that the title bar gets lost behind the top panel ..almost.
All other kinds of window, which for me amounts to about 90% by usage, do show the title bar complete with close button.
Double clicking *just below* the top panel will unmaximize a directory window so that the close button can be accessed.
These windows can be closed from the overview too.

---

### Post by Frogs Hair on 2013-08-16
Most of this is applicable up to Gnome 3.6. [https://wiki.gnome.org/GnomeShell/CheatSheet](https://wiki.gnome.org/GnomeShell/CheatSheet)

---

### Post by PJs Ronin on 2013-08-16
> **rotation2 said:**
> 
10)
How do I enable themes?
what is the difference between shell theme and current theme?
for shell theme I have to install user-theme extension. I read a few articles about it. It appears to be in quite a bunch of repos, is there an official repo for it?


Theming is best done with the Gnome Tweak Tool... available from repos.   To install by command line:
```
sudo apt-get update
sudo apt-get install gnome-tweak-tool
```
In GTT you can then set aspects of themes. "Current Theme"  sets parameters for window borders whereas "GTK+ Theme" sets parameters for the overall look/feel of a window (I think there is a better way of expressing this, but that's what I've come up with). You can also select an icon set from within GTT.

---

### Post by kurt18947 on 2013-08-17
For switching between browser windows and programs, I installed tint2 panel from the repositores.  It puts a hidden config folder in home editable with a text editor.  I  remove the clock, set it to autohide on smaller screens etc.  Gnome-tweak-tool to restore traditional minimize/window/close buttons.  If you haven't explored extensions.gnome.org, I'd recommend doing so.  No numlock/capslock indicator on wireless keyboards? Want a weather applet?  There's an extension for that:).

---

### Post by Jonor on 2013-08-17
Just to mention that i tried the Gnome shell extension [Hide Top Bar]("https://extensions.gnome.org/extension/545/hide-top-bar/") and when the top bar is hidden the 
top part of directory windows is still missing so it is not simply behind the top bar but absent ..almost.
Double clicking just below the top of the screen still unminimizes.

---

### Post by RichardET on 2013-08-17
> **rotation2 said:**
> I have to switch to Gnome 3 and there are a few questions:

1) Are there close buttons when a window is maximized? 
I have seen none

2)
Is only the current open window shown in the program list in the task bar on top?
Is there another way to switch between programs as alt-tab and clicking on activities?

3)
clicking on activities is a little slow. I am running (testing) ubuntugnome in a Virtual machine right now.
Is there a way to speed the opening of activities up?



5)
How do I organize the order of favourite icons?

6)
How do I create own desktop Shortcuts, e.g drag firefox from activities to desktop?

7)
How do I switch to desktop quickly? is there a keyboard shortcut?

8)
Is the keyboard shortcut ctrl-alt-t to open a terminal working everywhere?
In every open program?

9)
Is there a way to add shortcuts to the taskbar (right of Activities left of open-window-list)?

10)
How do I enable themes?
what is the difference between shell theme and current theme?
for shell theme I have to install user-theme extension. I read a few articles about it. It appears to be in quite a bunch of repos, is there an official repo for it?

11)
How do I open a program using alt-f2 and root privileges?
gksudo, sudo gksu is not working.

Thanks

I tried to love GNOME 3.x, but I married Unity, and never looked back.

---

