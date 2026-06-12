---
title: "Keyborad problem with special characters"
date: 2007-10-26
forum: Desktop Environments
---

### Post by hfwittmann on 2007-10-26
I recently encountered a problem with keyboard input in Ubuntu, which has not yet completely gone away. When in Keyboard preferecens I pressed Reset to default when the problem began.

Since then the keyboard input of special characters such as the "at sign" does not work anymore. There was an accompanying erroe mesage which I will list below, and which I can get rid of, however the problem itself still persists.

**Here is the message**

 Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10300000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


[B]Now the required results 

The result of xprop -root[/B]

_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "de", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us", "de", ""



** The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd**
 
 layouts = []
 model = 
 options = [altwin      altwin:meta_win]
 overrideSettings = true
 
 Any ideas anyone? Would be really appreciated.
 
 Felix

---

### Post by hfwittmann on 2007-10-26
**I have now actually found a/the solution to the problem. ** I went through the Configuration of the  xserver-xorg menu again(!) using * sudo dpkg-reconfigure xserver-xorg* and in the keyboard section switched to the appropriate locale (de) with no variants.  Somehow I thought I could do this with *Keyboard Preferences -> Layouts *, however this does not seem to work in all cases. :( Anyway, sorry for any inconvenience caused

---

