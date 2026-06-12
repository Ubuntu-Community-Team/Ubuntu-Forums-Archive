---
title: "KDE System Settings Keyboard &amp; Mouse Hangs"
date: 2006-12-05
forum: Desktop Environments
---

### Post by jgindin on 2006-12-05
I did a clean install of Ubuntu 6.10 last week. On top of that, I installed kde-desktop.

It seems that most (95%?) of the time, when I open the KDE System Settings (K  Menu -> System Settings) and click on the "Keyboard & Mouse" icon, I'm left with a busy cursor forever, or at least until I choose to terminate the systemsettings process.

I've tried running 'systemsettings' from a konsole to see if there's any useful output. The first thing I see immediately after starting the rocess is:
```

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

After clicking on the "Keyboard & Mouse" icon I see:

```

adding Keyboard /usr/share/applications/kde/keyboard.desktop

```

I've checked, and that does seem to be a valid file (13K).

I've tried running the "Keyboard" application from the K Menu -> Settings -> Peripherals -> Keyboard, but nothing happens beyond my cursor changing to a bouncing keyboard icon for a few seconds. (I tried right-clicking it to put it into a run dialog so I could see exactly what command was being invoked, but no luck...it just executes.)

I get the same behavior when I try to run the K Menu -> Settings -> Regional & Accessibility -> Keyboard Shortcuts, and a few others.

Like I said at the beginning, sometimes this stuff *does* work, though I'm not sure of exactly what circumstances it'll decide to do so.

I'd appreciate any help and/or pointers; I realize that there's not a whole lot of information here for debugging purposes; I'm more than happy to grab some additional "diagnostics" if someone has a suggestion on what additionally could help figure out what's gone wrong.

Thanks for the help,

jay

---

