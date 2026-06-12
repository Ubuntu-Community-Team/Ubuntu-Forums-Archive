---
title: "xmonad float window by title"
date: 2008-08-22
forum: Desktop Environments
---

### Post by e404 on 2008-08-22
Hi!

I write a game which creates 800x600 window. As you know, xmonad dictates size of every new window when it appears. So after launching this game it has invalid size. I cannot code because of it.

I tried to make it float in front of all other windows (emacs, launching-console, git-console), but unsuccessfully.

As far as I know I should make a rule or a hook for floating. It doesn't have WM_CLASS, only WM_NAME:
```
maciek:~$ xprop
WM_ICON_NAME(STRING) = "Hipmunk"
WM_NAME(STRING) = "Hipmunk"
WM_STATE(WM_STATE):
                window state: Normal
                icon window: 0x0
WM_NORMAL_HINTS(WM_SIZE_HINTS):
WM_PROTOCOLS(ATOM): protocols  WM_DELETE_WINDOW, _NET_WM_PING
```
"Hipmunk" is title of my game.

So I tried to set a rule for floating by title:
```
myManageHook = composeAll . concat $
    [ [ title       =? t                 --> doFloat | t <- myOtherFloats] ]
    where
        myOtherFloats   = ["xclock", "Hipmunk"]
```

But it doesn't work, I don't know why, because xclock sets itself to float layer.

Can somebody help my developing my game?
Best solution would be pointing a mistake in my config file, but also saying how to set WM_CLASS would be good solution. Thanks in advance.

I am running Archlinux, Xmonad version is 0.7.


Some helpful guy on gentoo forums solved my problem:
[http://forums.gentoo.org/viewtopic-p-5192240.html#5192240](http://forums.gentoo.org/viewtopic-p-5192240.html#5192240)

---

