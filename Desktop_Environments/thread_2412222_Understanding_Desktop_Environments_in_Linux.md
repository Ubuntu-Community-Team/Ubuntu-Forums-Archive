---
title: "Understanding Desktop Environments in Linux??"
date: 2019-02-09
forum: Desktop Environments
---

### Post by blown2bytes on 2019-02-09
I'm fairly new to Linux (using Ubuntu for a couple of years now) and I'm confused about the desktop environment in Linux. I read about terms such as display manager, x server, terminal server, TTYs, and desktop environments. It's confusing to me. Is there a good article somewhere or can someone explain to me what all these pieces do and how they interact together?

Specifically What is Display manager vs. X server vs. Desktop Environment.

Also, what is the difference between the "Ubuntu", "Ubuntu on Wayland", and "Unity" desktop environments.

---

### Post by CatKiller on 2019-02-09
> **blown2bytes said:**
> Specifically What is Display manager vs. X server vs. Desktop Environment.

The display manager simply provides the graphical login screen at the end of the boot process and launches the next stage when you log in. Examples would be GDM, LightDM, SDDM.

The X server handles the display and keyboard and mouse input. It is 35 years old and somewhat crufty. Wayland is the more modern replacement, but is a work-in-progress. Not all of the things that the X server can do can be done in Wayland yet.

The window manager handles the decoration and placement of windows. Examples would be Mutter, KWin, Compiz, Muffin.

A desktop environment is a collection of applications to work together. This will generally include a window manager, a default display manager, and a set of default applications. Examples would be Gnome, KDE, Cinnamon, Xfce. Unity acted like a desktop environment, but was based on Gnome applications. It was a set of plugins for Compiz and a standard configuration. Unity has since been discontinued as a Canonical project in favour of configuring Gnome to act largely the same way.

You can broadly chop-and-change as you see fit. For example, my old system was using the X server, LightDM to log in, Compiz as the window manager, and various Gnome and KDE applications.

The TTYs are virtual teletypes. They are text-only. You can access them by using Ctrl-Alt-F1 through Ctrl-Alt-F7. You will generally have your graphical environment taking up one of those slots. They are useful for troubleshooting and for nerd-cred.

---

### Post by dmnur on 2019-02-09
My two cents.

**TTY** is an abbreviation for "teletype". Unix (Linux is a Unix-like operating system) is pretty old, and originally people used teletypes as their terminals. The output was printed to paper. See [Wikipedia article](https://en.wikipedia.org/wiki/Teleprinter). Then video display terminals replaced teletypes completely, but the term stuck. Nowadays most of time TTY means a virtual terminal ([wiki](https://en.wikipedia.org/wiki/Virtual_console)) one can see when X server isn't running.

**X server** is a program that implements the X protocol with which graphical applications (X clients) communicate. More info [here](https://en.wikipedia.org/wiki/X_Window_System). Linux uses X for all fancy graphical output.

**Display manager** is a program used to manage graphical logins and start X sessions. This is the graphical login screen you see after boot.

**Desktop environment** is a suite of graphical programs that are integrated to provide a certain look and feel. Window manager, panels, menus, desktop icons, file manager etc. Briefly it's a window manager + applications. There are ready-to-use desktop environments like GNOME, KDE, XFCE, LXDE. One may also assemble his own desktop environment by installing every component himself.

**Terminal server** is a computer to which so-called thin clients connect. Think of it as a remote desktop for multiple users, each with his own desktop. Its primary use is to save money: a company could buy one high-performance server and many low-performance user workstations, and these workstations would only be used to connect to this server and work there remotely.

---

### Post by Frogs Hair on 2019-02-09
[Wayland vs Xorg]("https://www.secjuice.com/wayland-vs-xorg/")

---

### Post by blown2bytes on 2019-02-11
Thanks for the information..

---

### Post by Claus7 on 2019-02-22
Hello,
> **blown2bytes said:**
> Thanks for the information..
+1

[EDIT]
checking display manager:
```
cat /etc/X11/default-display-manager
```

checking graphical session:
```
loginctl show-session `loginctl | grep <YOUR_USER_NAME> | awk '{print $1}'` -p Type
```

checking window manager: 
```
wmctrl -m
```

checking desktop environment:
```
env | grep DESKTOP_SESSION=
```

Regards!

---

