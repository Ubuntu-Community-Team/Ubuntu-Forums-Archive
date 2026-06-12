---
title: "Switching windows"
date: 2013-03-11
forum: Desktop Environments
---

### Post by edivad on 2013-03-11
good evening everyone,

I've installed 12.10 on Macbook2,1 with 1GB ram. Unity was working but due to hardware restrictions I had to install gnome-sessions-fallback and going back to previous gnome.

in this environment it's usable but I can't have the Switching Windows Shortcut working. When I press the Alt+Tab the windows are not switching. If I open the Keyboard settings, in the shortcuts->navigation I have Alt+Tab selected. I tried changing with different combinations but none of them is working.

Any ideas?

Thank you 
Regards
Davide

---

### Post by ajgreeny on 2013-03-11
Are you using classic gnome with or without desktop effects?  Try without effects and you may find everything works as expected.

If you are not using unity you don't really need compiz anyway.

---

### Post by tgalati4 on 2013-03-11
Alt-tab will switch between several windows open in the same workspace.  Control-Alt-Arrow (left or right) will switch the workspace to the left or right.

---

### Post by edivad on 2013-03-12
> **ajgreeny said:**
> Are you using classic gnome with or without desktop effects?  Try without effects and you may find everything works as expected.

If you are not using unity you don't really need compiz anyway.

thanks ajgreeny. Switching to "No effects" at all solved the issue... Strange though :)

---

### Post by stinkeye on 2013-03-12
There are a couple of switchers in compiz.
Unity uses the one in the unity plugin for compiz.

The unity plugin for compiz is disabled in the gnome classic session and therefore no switcher.
You need to enable the old switcher in ccsm.
If the old switcher does not show in ccsm, install the **compiz-plugins** package.
If you don't like or use the other stuff provided by compiz, just do as **ajgreeny** said.

---

