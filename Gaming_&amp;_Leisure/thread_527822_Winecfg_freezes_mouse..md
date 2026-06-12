---
title: "Winecfg freezes mouse."
date: 2007-08-17
forum: Gaming &amp; Leisure
---

### Post by digitalsonata on 2007-08-17
As the title says my mouse freezes when I run winecfg. ctrl-alt-backspace does not work and just hangs at a blank screen, removing and plugging the mouse back in does not work. Only restarting the computer helps. 

Ubuntu 7.04
Wine 9.43
Mouse: Logitech MX518
Motherboard: Asrock 939Dual-Sata2
CPU: AMD 64 3200+ Venice
RAM: Kingston 2gb PC3200
Graphics Card: Nvidia XFX 7600GT

Any help would be appreciated.

---

### Post by digitalsonata on 2007-08-18
Bump :\

---

### Post by cogadh on 2007-08-18
Have you tried removing/reinstalling Wine? Are you using the 64-bit version of Wine?

---

### Post by digitalsonata on 2007-08-18
No I haven't tried reinstalling, its strange though because I can run WoW perfectly but I just can't enter the config. I am using the 32bit version.

---

### Post by cogadh on 2007-08-18
You can uninstall/reinstall Wine without losing your current working configuration, just don't delete the .wine directory in your home directory.

I honestly don't know much about using 32 bit Wine on a 64 bit system, but it seems to me that might cause some problems. There is a 64 bit version of Wine available in the Wine repositories, you might try that.

Also, just to troubleshoot the problem, you could try renaming your .wine directory to something like ".wine-old" then re-run winecfg. That way Wine will re-create the whole configuration and .wine directory. Any configurations you may have that could be interfering with winecfg won't be there and maybe it will work. That would at least confirm or eliminate a potential source of the problem.

---

### Post by digitalsonata on 2007-08-18
I'm running the 32 bit version of Ubuntu, the last x64 distro I tried didn't exactly work that great >.<

I'll trying deleted the .wine directory now

Edit: Winecfg still froze the mouse, I remember now this also happened when using 9.33

---

### Post by cogadh on 2007-08-18
That's really odd. Do you have a unique type of mouse or mouse configuration?

---

### Post by digitalsonata on 2007-08-18
I edited my xorg.conf a bit to enable all the buttons on it

```

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "yes"
    Option         "ZAxisMapping" "4 5"
    [B]Option         "Buttons" "10"
    Option         "ButtonMapping" "1 2 3 6 7 8 9 10"[/B]
EndSection

```

Other than that I can't think of anything

---

### Post by cogadh on 2007-08-18
That shouldn't be a problem, but try commenting out those button mappings and see if it makes a difference.

---

### Post by digitalsonata on 2007-08-31
Update: I've been busy with classes and have not had time to work on this till today. My mouse broke and I'm using a different USB mouse. I uninstalled 9.43 and installed 9.44, winecfg no longer freezes my mouse. It all works so far, though I'm still curious about what caused the problem.

---

