---
title: "Apple USB keyboard not working"
date: 2006-06-04
forum: Desktop Environments
---

### Post by vladuz976 on 2006-06-04
Using apple USB keyboard. it initially works fine, after not using it for approximately 2 min, it stops working, completely dead. I've set my BIOS to USB keyboard and this is my keyboard section in xorg. What can I do to fix it?

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "USB Keyboard"
    InputDevice    "USB Mouse"
EndSection

Section "InputDevice"
    Identifier     "USB Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

```

---

### Post by FredB on 2006-06-04
Erh... I thought that apple keyboard are only usable with mac hardware ?!

Did you try to see in keyboard properties under gnome settings menu ?

---

### Post by vladuz976 on 2006-06-04
[QUOTE=FredB]Erh... I thought that apple keyboard are only usable with mac hardware ?!

Did you try to see in keyboard properties under gnome settings menu ?[/QUOTE]

Why would that be the case?
By the way I am not using Gnome. 
I am trying to get it to work in general not only in one specific wm.

---

### Post by black bear theory on 2006-06-13
[QUOTE=FredB]Erh... I thought that apple keyboard are only usable with mac hardware ?!

Did you try to see in keyboard properties under gnome settings menu ?[/QUOTE]
an apple keyboard is just a usb keyboard made by apple. i've used mine in gentoo, suse and even be.

but count me among those that can't get it to work with ubuntu. it was working last night (not sure what i did) but is no longer working today.

---

