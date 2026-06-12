---
title: "Tiling in LXDE (with or without xmonad)"
date: 2012-10-31
forum: Desktop Environments
---

### Post by oscarbenjamin on 2012-10-31
I'm new to Lubuntu/LXDE/openbox and I've just installed Lubuntu 12.10. I'm so far unable to find a way to tile windows with the keyboard.

Is there a way to have a keyboard shortcut that will make a window fill the left or right half of the screen (like in unity and Windows 7)?

Alternatively, I'm trying to get XMonad to work with Lubuntu. I've tried the instructions from
[http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_LXDE]("http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_LXDE") to no avail. I get compiler errors from the xmonad.hs file when logging in to an "Xmonad" session and if I try the windowmanager=xmonad suggestion then my "Lubuntu" session is broken (It shows my desktop background but no Lubuntu or Xmonad commands work so I have to reboot via the tty).

Does anyone know a way to get XMonad to work as the window manager within the "Lubuntu" session?


Thanks,
Oscar

---

### Post by vasa1 on 2012-10-31
> **oscarbenjamin said:**
> I'm new to Lubuntu/LXDE/openbox and I've just installed Lubuntu 12.10. I'm so far unable to find a way to tile windows with the keyboard.

Is there a way to have a keyboard shortcut that will make a window fill the left or right half of the screen (like in unity and Windows 7)?
...
[http://ubuntuforums.org/showthread.php?t=2068644](http://ubuntuforums.org/showthread.php?t=2068644)
[http://crunchbanglinux.org/forums/topic/13968/aero-snap-in-openbox/](http://crunchbanglinux.org/forums/topic/13968/aero-snap-in-openbox/)
[https://bbs.archlinux.org/viewtopic.php?id=93126](https://bbs.archlinux.org/viewtopic.php?id=93126)

---

### Post by oscarbenjamin on 2012-11-01
> **vasa1 said:**
> [http://ubuntuforums.org/showthread.php?t=2068644](http://ubuntuforums.org/showthread.php?t=2068644)
[http://crunchbanglinux.org/forums/topic/13968/aero-snap-in-openbox/](http://crunchbanglinux.org/forums/topic/13968/aero-snap-in-openbox/)
[https://bbs.archlinux.org/viewtopic.php?id=93126](https://bbs.archlinux.org/viewtopic.php?id=93126)

Thanks vasa1. Following the second link you posted (crunchbanglinux) I found the exact solution for what I wanted. Here it is:

```
    <!-- Fill left half of desktop -->
    <keybind key="C-W-Left">
      <action name="Unmaximize"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <height>99%</height>
        <width>50%</width>
      </action>
    </keybind>
    <!-- Fill right half of desktop -->
    <keybind key="C-W-Right">
      <action name="Unmaximize"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <height>99%</height>
        <width>50%</width>
      </action>
    </keybind>

```

With the above in ~/.config/openbox/lubuntu-rc.xml I can position main windows to the left/right half of the screens with Control-Super-Left/Right as in unity.

Thanks again.

---

### Post by Pirate Zoro on 2012-11-01
Since your question has been answered, you should mark this thread as solved.

---

### Post by oscarbenjamin on 2012-11-01
> **Pirate Zoro said:**
> Since your question has been answered, you should mark this thread as solved.

Sorry, I'll work out how to do that now.

---

