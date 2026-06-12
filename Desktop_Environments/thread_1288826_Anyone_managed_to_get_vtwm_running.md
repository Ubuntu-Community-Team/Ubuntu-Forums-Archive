---
title: "Anyone managed to get vtwm running?"
date: 2009-10-11
forum: Desktop Environments
---

### Post by J05HYYY on 2009-10-11
Hello.

I downloaded vtwm and typed the command into a terminal.

It said:
```

vtwm:  another window manager is already running on screen 0?
vtwm:  unable to find any unmanaged screens

```

So then I tried to add this to /usr/share/xsessions/vtwm.desktop and login, selecting the session

```

[Desktop Entry]
Encoding=UTF-8
Name=vtwm
Comment=
Exec=vtwm
Icon=
Type=Application
CTRL-D

```

... but that didn't work either (I guess it was meant for twm only)

so then I pressed CTRL+ALT+F1 and typed "vtwm"

```
vtwm: unable to open display ""
```

Now I'm stumped. Any ideas?
I couldn't find any documentation at all.

---

### Post by J05HYYY on 2009-10-14
Hello, I finally managed to get vtwm running but it's looking pretty horrible!

I created/edited "~/.xinitrc", then created a symbolic link "ln -s ~/.xinitrc ~/.xsession".

This sort of worked but looked nasty.

[For more information click here.]("http://en.gentoo-wiki.com/wiki/X.Org/xsession")


_______________________________________________________________

I also realised that fbpanel did not show applications in the taskbar. I assume it's because it is not NetWM compliant. I am going to try fvwm instead.

---

