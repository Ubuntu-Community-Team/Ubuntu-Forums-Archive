---
title: "Mouse/Keyboard"
date: 2009-03-10
forum: General Help
---

### Post by Kyle5 on 2009-03-10
Ok I need help ASAP. I have been looking around everywhere for this problem and nothing has helped. The problem is when I load Ubuntu 8.10 I cannot move my mouse or my keyboard. I have tried Alt+Ctrl+f2 and Alt+Ctrl+f1 yes they work. And I can also type with my keyboard. When I did the upgrade from 8.04 to 8.10 this happend to me. I hear this is a common bug but I need to fix it if anyone has any ideas. Another thing I can do is downgrade to 8.04 which I'd need help with because I don't have the Live Cd because I borrowed it from a teacher. I can't download it either because I don't have a cd. If there is a way to do it through flashdrive through windows this would help. The frusterating thing is I've been having troubles for 5 days now. All different although this did happen once but I thought it was a corrupt installation, so I downloaded again. Please help ASAP.
Thanks so much

---

### Post by Kyle5 on 2009-03-10
Bump

---

### Post by Kyle5 on 2009-03-10
Anyone?

---

### Post by cubeist on 2009-03-10
if you want help, you have to provide some details...
for example, are your keyboard/mouse recognized in lspci?
are they wireless (bluetooth), or wired... and once you have booted to your desktop, if you unplug and then plug in your keyboard does it start working?, same with the mouse?

---

### Post by Kyle5 on 2009-03-10
No it doesn't work when I unplug/plug it in. It works when I try Alt+Ctrl+f1/f2 at the login screen. But that is command line I beleive. It allows me to log in from there and make commands. There wired, I have tried other keyboards and other mouses. No luck, I hear this is a common bug for upgrading to 8.10. Looking for people who know how to fix it.

---

### Post by Defrector on 2009-03-10
I'm clueless, but just throwing ideas into the fire until someone smarter comes along:

Seeing that you can type from the text-console mode, your keyboard (and maybe your mouse) work at the hardware level; it sounds like X11 (the GUI system) is having some sort of issues with your peripherals, so your X configuration might be a good place to look. Also try a search on "X11 keyboard mouse dont work" or something like that and see what comes up.

Best of luck! :KS

---

### Post by cubeist on 2009-03-10
If you know it is a bug in Ubuntu, then search launchpad for it ad read the comments to see if there is a fix...

Or try using the generic encapsulation in your xorg.conf file

boot into a recovery session, backup your xorg.conf file, then change the keyboard and mouse sections to:
```
Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection
```

If this works, then you can graphically use the keyboard preference pane to select your actual model... but without knowing that, I can't really help you further...good luck

---

### Post by Kyle5 on 2009-03-10
Ok thanks I'll try that any other ideas?

---

