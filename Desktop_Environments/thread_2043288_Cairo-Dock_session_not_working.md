---
title: "Cairo-Dock session not working"
date: 2012-08-16
forum: Desktop Environments
---

### Post by newb85 on 2012-08-16
I just installed Cairo-Dock, and was thrilled with the improvements since I last used it a few years ago.  I especially like how it has its own sessions available at login.

The Cairo-Dock session worked great the first time, but since then, it has been launching both Cairo-Dock and Unity (a very messy and unsatisfying experience).

Any thoughts as to why this is happening?

I'm running vanilla Ubuntu 12.04 with Gnome also installed.

Thanks!

---

### Post by Frogs Hair on 2012-08-16
I experimented with the Cairo Dock Session on 11.10 and 12.04 . It is a PPA and subject to problems and while the 11.10 experience was a good one I ended up reinstalling 12.04 when using it. When trying to remove the Cairo Dock Plug-ins from synaptic my entire Ubuntu desktop and all applications were removed in the process. Be careful to purge the PPA properly if you remove it.

---

### Post by newb85 on 2012-08-16
Well, I'm not to the point of uninstalling, yet.  It isn't working right, but it isn't hurting anything else.

Okay, I didn't add a ppa to install it.  It showed up in Synaptic, so I assumed it came from the main repos, but I have added other repos.  Is there a way to determine which repo it installed from?

Also, I realized it isn't accurate to call my system vanilla Ubuntu.  I'm running a patched Unity for Dodge and minimize-on-click.  This hasn't caused issues for Gnome sessions, though.

---

### Post by Frogs Hair on 2012-08-16
This is the PPA I used and the source would be found in software sources.[http://www.noobslab.com/2012/04/install-cairo-dock-30-on-ubuntulinux.html](http://www.noobslab.com/2012/04/install-cairo-dock-30-on-ubuntulinux.html)

---

### Post by newb85 on 2012-08-16
According to Synaptic, I got Cairo-Dock from the Universe.

---

### Post by Frogs Hair on 2012-08-16
The version in the software center is supposed to be compatible with Unity. If you are logged into Ubuntu or Ubuntu 2D and have the dock set to auto start you would see both Unity and Cairo Dock. If you are not logged into a Ubuntu session I don't know why Unity would be starting.

---

### Post by newb85 on 2012-08-17
The problem is with the Cairo-Dock (Gnome + Effects) session.

Here are the contents of the corresponding desktop session file (/usr/share/xsessions/cairo-dock.desktop):
```

[Desktop Entry]
Name=Cairo-Dock (Gnome + Effects)
Comment=This session logs you into GNOME with Cairo-Dock and with graphical effects.
Exec=gnome-session --session=cairo-dock
TryExec=cairo-dock-session
Icon=
Type=Application
```And the contents of the session file that is called with the gnome-session command (/usr/share/gnome-session/sessions/cairo-dock.session):
```
[GNOME Session]
Name=Cairo-Dock Session
RequiredComponents=gnome-settings-daemon;
RequiredProviders=windowmanager;panel;
DefaultProvider-windowmanager=compiz
DefaultProvider-panel=cairo-dock
IsRunnableHelper=/usr/lib/nux/unity_support_test
FallbackSession=cairo-dock-fallback
DesktopName=GNOME
```Comparing this with ubuntu.session, I notice that there the line is
```
DefaultProvider-panel=compiz
```instead.  (Apparently, calling compiz as the panel provider is supposed to call unity?)  Could this possibly have something to do with the fact that compiz is being called as a window manager, even in the C-D session?  Or perhaps the line about unity_support_test shouldn't be there?

---

### Post by Frogs Hair on 2012-08-17
Cairo Dock will work with Compiz and Unity 3D is also a Compiz plug-in  so disabling the Unity plug-in in the CCSM may be a work around until you wanted to use a Ubuntu session

---

### Post by Frogs Hair on 2012-08-17
If you have the Compiz icon on the dock it will start Compiz when the dock starts and probably the Unity plug-in as well when open GL is in use.

---

### Post by newb85 on 2012-08-17
> **Frogs Hair said:**
> Cairo Dock will work with Compiz and Unity 3D is also a Compiz plug-in  so disabling the Unity plug-in in the CCSM may be a work around until you wanted to use a Ubuntu session

Wow, your suggestion came really close to the solution.  Actually, I think it came really close the the origin of the problem.  I would be leaping for joy right now, if I weren't hanging my head in shame.

Compiz saves its settings to profiles.  Different desktop sessions can run on different profiles.  Apparently, a Cairo-Dock session is accomplished by setting up a Compiz profile (called Default) that excludes Unity.  

When I first tried the Cairo-Dock session, I was giddy about the freedom to play with CCSM without fear of interfering with the ever-so-tempermental Unity plugin.  (I still have nightmares about the time I wrecked my Natty setup this way.)  And apparently, while I was examining the Preferences section of CCSM, I inadvertently switched to the unity profile.  ](*,)  Simply switching it back rectified the problem.

---

