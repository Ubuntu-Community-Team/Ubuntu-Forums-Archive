---
title: "compiz fusion crashes :("
date: 2007-09-15
forum: Desktop Effects &amp; Customization
---

### Post by gorgeous_george on 2007-09-15
well, hi guys!
having troubles with compiz fusion. I run ubuntu 7.04 w/ kernel 2.6.20-16 on a IBM thinkpad R60, with integrated intel graphics. compiz fusion worked fine till last week, when I formatted my hd and re-installed ubuntu. Now when I open GL desktop, it says me :
```
An error occurred while loading or saving configuration information for gnome-compiz-preferences. Some of your configuration settings may not work properly.
```

and these are the details of the error message:
```
Type mismatch: Expected list, got string
Type mismatch: Expected list, got string
Type mismatch: Expected list, got string
```

everyway, if I enable gl desktop, all effects become active, but they're very slow, and if I drag a window, X crashes and only the mouse still moves. still I can load the terminal or close windows, but i cannot interact with the desktop trough the mouse.
That's all folks! Thanks in advance for your help.
bye

---

### Post by DrewBoo on 2007-09-18
I'm experiencing the same symptoms.  Home-assembled computer, just removed Beryl to try Compiz-Fusion.

Identical error message (three "Expected list, got string").

Identical symptoms.  Very slow, with a freeze when I try to move a window.  Mouse cursor is still responsive.

I'll post any solutions I come up with, though help would be greatly appreciated.

---

### Post by daicoden on 2007-09-21
I have the exact same symptoms....

I'm using emerald as the window manager and it pops up ok if i disable the gl desktop and re enable it.

My system has a real hard time opening even windows (not Microsoft), stray marks are left across the screen.  I am using a Radeon X1300.  I know the graphics card should be able to handle it because i used openGL and directX except on the machine when it had windows (Microsoft).

But it's wierd I have the exact same 3 list expected got string and then i try to move a window and everything locks up except the mouse.

Thank you any pointers would be apreciated!

---

### Post by Forlong on 2007-09-21
Don't use "GL Desktop" with Compiz Fusion - it's designed only to work with Compiz core and the main plugins.

Use ccsm from the package **compizconfig-settings-manager** instead.

---

