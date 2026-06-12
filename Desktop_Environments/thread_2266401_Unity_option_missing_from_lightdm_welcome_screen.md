---
title: "Unity option missing from lightdm welcome screen"
date: 2015-02-22
forum: Desktop Environments
---

### Post by halfbeing on 2015-02-22
Unity is missing from the list of available desktop environments in my lightdm welcome screen.

I originally installed UbuntuStudio on my machine and used the default XFCE, but then I installed Unity and it worked. However I had some problems with it and I went back to XFCE. I think in the process I may have uninstalled some stuff. Since then my needs have changed and I want to use Unity again, but it isn't offered as an option in the welcome screen any more. I have installed unity, unity8 and ubuntu-desktop, which I thought would pull in everything unity-related that I might have deleted, but I still can't find Unity on the welcome screen. Does anyone know what I am missing?

---

### Post by Frogs Hair on 2015-02-23
> [COLOR=#000000]I have installed unity, unity8 and ubuntu-desktop[/COLOR]

Unity 8 is an experimental package for the Mir display sever still in development , so I would start by removing it .

---

### Post by deadflowr on 2015-02-23
> Does anyone know what I am missing?

Having no idea which version of Ubuntu, 14.04 and up have a session package called ubuntu-session.
Prior versions ,aka 12.04, used gnome-session (or some variant), instead.

See if that's what was missing?

---

### Post by halfbeing on 2015-02-23
Thanks for your replies.

I'm using 14.10. I've got ubuntu-session installed.

---

### Post by deadflowr on 2015-02-23
Okay, somewhat crypted as to whether you already had ubuntu-session installed or you just installed it( I think you meant it was already installed), but it matters not...
Do you have an entry in /usr/share/xsessions for ubuntu.desktop?
(Unity's login name is actually Ubuntu, and the xsession is ubuntu)

Also, you state you have xfce installed, are you running the lightdm-gtk-greeter(looks like an older login screen), or are you running unity-greeter? (the one that you see with unity that has the login name and password box at the left side area of the screen)
I'm not sure if this is at all relevant, but just in case, it might be helpful...

---

### Post by halfbeing on 2015-02-23
Yes I do have an entry for ubuntu in /usr/share/xsessions. I am using the lightdm greeter.

---

### Post by egeezer on 2015-02-23
In your Xfce session, check the right-hand corner of the top panel.  If you mouse-over (it might work, I don't recall) or right-click some of the icons you might find one that gives you a drop-down that offers the desktop options.

---

### Post by halfbeing on 2015-02-24
I've done that. There are entries for Gnome, XFCE and UbuntuStudio, but not for Unity.

---

### Post by deadflowr on 2015-02-24
post the output for
```
cat /usr/share/xsessions/ubuntu.desktop
```

---

### Post by halfbeing on 2015-02-24
[COLOR=#000000][FONT=Ubuntu Mono]cat /usr/share/xsessions/ubuntu.desktop[/FONT][/COLOR]
```

[Desktop Entry]
Name=Ubuntu
Comment=This session logs you into Ubuntu
Exec=gnome-session --session=ubuntu
TryExec=unity
Icon=
Type=Application
X-LightDM-DesktopName=Unity
X-Ubuntu-Gettext-Domain=gnome-session-3.0

```

---

### Post by deadflowr on 2015-02-24
Hmm, that should make Ubuntu show in the greeter.
You do mention gnome shows, but did not mention installing gnome.
Is it really gnome, or perhaps a misnamed file...
Somewhat curious me is.

---

