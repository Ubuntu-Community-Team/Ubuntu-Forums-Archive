---
title: "fluxbox + xcompmgr"
date: 2009-02-03
forum: Desktop Environments
---

### Post by norkbes on 2009-02-03
Hi,

I have a problem with transparency with fluxbox. The configuration of X.org seems to be ok:

$ xdpyinfo | grep -i -E 'Composite|Render'
    Composite
    RENDER

yet, when I run xcompmgr -c all what I can see is conky and my wallpaper (set with feh). Transparency works when I start switching between open windows (TAB), then transparent windows disapear.

Do you have any ideas what should I fix?

Regards,
chris

---

### Post by m_duck on 2009-02-03
What is the problem specifically? Xcompmgr will not make everything transparent, it just enables things to do so. I have xcompmgr launched from my autostart file (though in openbox but assume fluxbox is similar).

With xcompmgr running, you can enable transparency in programs, e.g. in gnome-terminal you can Edit -> Current Profile -> Effects Tab then Transparent Background and adjust the slider for the level of transparency required. For some programs which do not have transparency options, there is a program called transset. I've not used it for ages, but from memory, you can launch certain programs which certain transparencies. E.g. (take this with a pinch of salt) I believe you could get transparency in gedit for example using```
transset <options> gedit
```<options> being where you would set transparency level and such like. Check the man page for transset after installing it to see```
man transset
```

---

### Post by norkbes on 2009-02-04
Concerning transparency in fluxbox I strictly followed instructions in 

```
http://fluxbox-wiki.org/index.php?title=Transparency
```

i.e. I configured Xorg accordingly and used transset as you mentioned. I even modified fluxbox init file:

```

session.screen0.window.focus.alpha:     128
session.screen0.window.unfocus.alpha:   64 
session.screen0.toolbar.alpha:  255
session.screen0.slit.alpha:     255
session.screen0.menu.alpha:     255

```

Now, the problem is that application windows (firefox, uXterm, etc.) are visible (i.e. transparent) only if I use them, i.e. type in commands or switch between them. If they are inactive you cannot find them on the desktop. The only visible elements are the wallpaper (displayed with feh) or one-colour background and conky (system monitor) running. Both icons (idesk), fbpager, and iconbar disappear.

---

