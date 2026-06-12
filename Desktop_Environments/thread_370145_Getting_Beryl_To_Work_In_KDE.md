---
title: "Getting Beryl To Work In KDE?"
date: 2007-02-25
forum: Desktop Environments
---

### Post by Dylnuge on 2007-02-25
I just tried installing Beryl using the script available at this site:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)

I accidentally used the one for Ubuntu instead of Kubuntu (not thinking, since my system still says Ubuntu and I forgot that Kubuntu essentially means KDE).

Beryl loads under both KDE and GNOME with this installation. It does not do anything-no effects, no themes, no nothing. When I click on the icon and change Window Manager to Beryl, it does not work, and switches back to KWin (fallback manager). Should I uninstall and try again? How?

Thanks,
Dylan

When Running Beryl command in Terminal:
```

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension

```

PS: How, if possible, can I add a network monitor icon to KDE like I have in GNOME?

---

### Post by shareMenaPeace on 2007-02-25
See my signature for uninstalling /reinstall beryl.

---

### Post by Dylnuge on 2007-02-25
Tried it, thanks.

Still getting this error message when typing beryl into the terminal:
```
Checking for XComposite extension               : failed
```

---

### Post by Dylnuge on 2007-02-25
After uninstall/reinstall Window Decorator options are grayed out, but emerald is still there.

Please help.

---

### Post by amphet on 2007-02-25
right click beryl icon > select window manager > beryl

see if that helps

---

### Post by Dylnuge on 2007-02-26
That's what I have been doing (in addition to running beryl from shell to get verbose response). Beryl crashes and returns to default fallback WM (KWin in my case).

Running in command line produces above verbose message.

---

### Post by Dylnuge on 2007-02-26
In case it helps, I get this error a lot when running anything verbose in the shell. So much that I have learned to ignore it, as there don't seem to be any problems.
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

---

