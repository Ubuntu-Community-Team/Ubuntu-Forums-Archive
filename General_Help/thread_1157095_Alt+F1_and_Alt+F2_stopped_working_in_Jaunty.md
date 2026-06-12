---
title: "Alt+F1 and Alt+F2 stopped working in Jaunty"
date: 2009-05-12
forum: General Help
---

### Post by ruffneck on 2009-05-12
Ever since I upgraded from Intrepid to Jaunty, I no longer have the ability to launch the "Run" dialog box with Alt+F2 - nothing happens. I checked System > Preferences > Keyboard Shortcuts and Alt+F2 is set to open the "Run" dialog box. 

The only change I made that could be related was to edit my Xorg file to enable Ctrl+Alt+Backspace. 

Anyone have an idea why this has happened. I'm stumped and can't find any information regarding this.

---

### Post by Brandon Williams on 2009-05-12
IIRC, I was having this same problem on one of my machines after the install. I changed the keyboard shortcut for the run dialog and then changed it back and it started working fine after that.

---

### Post by ruffneck on 2009-05-12
Hey Brandon, your reply is much appreciated, I'll give that a try and see what happens.

---

### Post by ruffneck on 2009-05-12
Changing the Keyboard Shortcut for the "Run" Dialog Box and changing it back doesn't work for me. Does any one else have ideas I could try?

Thanks in advance.



-

---

### Post by pathorn on 2009-05-24
You can try setting
Option "DontVTSwitch" "off"
Option "AllowDeactivateGrabs" "on"
Option "DontZap" off"

I was not able to get those working, but since you mention that you managed to fix ctrl-alt-backspace, then you have a chance.

If not, Alt-Sysrq-r should work as a last resort. It takes the keyboard out of raw mode, allowing plain Alt-F1 and Alt-F2 to work the same way as in the kernel.  This change remains permanaently until you restart the x server, so any programs that require alt+f-keys will stop working. One obvious example of this is the "Alt-F4" shortcut to close programs, which will now switch to VT #4 instead. But in some cases it is worth the tradeoff. This won't enable ctrl-alt-backspace or ctrl-alt-+/- either.

---

### Post by m_duck on 2009-05-24
The only time I have found Alt F1 and Alt F2 not working is when using recent versions of compiz. Open up ccsm (can't remember which menu it's in - you can run ccsm from terminal though) and look for "Gnome Compatibility" and enable it and that should solve the problem. If you don't have ccsm installed, install it with:```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by dccrens on 2009-05-29
> **m_duck said:**
> The only time I have found Alt F1 and Alt F2 not working is when using recent versions of compiz. Open up ccsm (can't remember which menu it's in - you can run ccsm from terminal though) and look for "Gnome Compatibility" and enable it and that should solve the problem. If you don't have ccsm installed, install it with:```
sudo apt-get install compizconfig-settings-manager
```

I have the alt+f2 issue as well. However, I can't find "Gnome Compatibility" in the compizconfig-settings-manager. Any ideas where it is located?

---

### Post by CatKiller on 2009-05-29
> **dccrens said:**
> I have the alt+f2 issue as well. However, I can't find "Gnome Compatibility" in the compizconfig-settings-manager. Any ideas where it is located?

In the General section, with Commands and General Options.

---

### Post by dccrens on 2009-05-29
> **CatKiller said:**
> In the General section, with Commands and General Options.
CatKiller,

Nothing on that page except keybinding and commands. Nothing about "Gnome Compatibility"...

---

### Post by CatKiller on 2009-05-30
Are you running Jaunty? I don't recall seeing it in Intrepid.

---

### Post by dccrens on 2009-06-18
> **CatKiller said:**
> Are you running Jaunty? I don't recall seeing it in Intrepid.

Catkiller,
I am still on Intrepid... Still haven't found any solution...

---

### Post by aravindprasad on 2010-04-14
This is probably the stupidest solution to this problem but this happened to me and I realized the solution after 3 weeks of frustration. So here it goes for reference to others.

I have a *^&%* **Microsoft keyboard** attached to my Ubuntu box at work (don't ask why). And it has this key called **F-Lock** which functions similar to CapsLock - you hit it to turn it on and hit it again to turn it off. Basically when F-Lock is off, the function keys have predefined functions like F1 is help, F2 is undo, etc. And these functions work in Linux too. When F-Lock is on, the same keys work as function keys in addition to the predefined functions above. And only in the On mode will you be able to use the function keys for multiple key combinations (like TADAA Alt+F2). 

My key combinations involving any function key were not working after the upgrade to Jaunty because the F-Lock key somehow got turned off. And having never encountered such a f***all useless key till then, it never occurred to me till one day I hit it by mistake instead of the print screen key.

Now I have no clue why we need this arrangement when all the function keys can simply have predefined functionality which can be reprogrammed. I think the designers of this keyboard at **Microsoft** had their **kidneys** and **brains** **interchanged** to come up with such a useless and troublesome "feature"

-AP

---

