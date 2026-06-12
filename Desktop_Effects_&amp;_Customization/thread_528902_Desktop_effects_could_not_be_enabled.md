---
title: "Desktop effects could not be enabled"
date: 2007-08-18
forum: Desktop Effects &amp; Customization
---

### Post by mmmkile on 2007-08-18
I was running Xine player on Ubuntu 7.04 and I switch to the full screen mode.

As I switched back to normal screen view, the computer locked up and i couldn't do anything.

I had to shut down the computer by force. I started the computer back up, and enabled Beryl.

But the effects of Beryl would not show up.
I tried to enable desktop effects by System>Preferences>Desktop Effects, and I receive an error message say "Desktop Effects Could Not Be Enabled".

Keep in mind this is the first time this has happened and both have worked before.

---

### Post by Happy_Man on 2007-08-18
Hmmm.... start Desktop Effects with the terminal, see what comes up? I think the command is ```
desktop-effects
```

---

### Post by mmmkile on 2007-08-19
nvidia hardware not available
gtk-window-decorator: Could not acquire decoration manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
gtk-window-decorator: Could not acquire decoration manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by Happy_Man on 2007-08-19
> **mmmkile said:**
> nvidia hardware not available
gtk-window-decorator: Could not acquire decoration manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
gtk-window-decorator: Could not acquire decoration manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Why's it say "nvidia hardware not available"? Did you swap video cards?

---

### Post by bir7 on 2007-08-21
The same error message for me too under xgl-session with ati-x1800. 
It's a bit suspect, because compiz fusion and desktop-effects have worked before too.

It could be the a ATI driver problem. But i am not sure.
I found this bug [https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/131141](https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/131141)
in Gutsy.

---

