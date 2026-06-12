---
title: "Avant Window Navigato"
date: 2008-08-27
forum: Desktop Environments
---

### Post by SikEnCide on 2008-08-27
When I attempt to install Avant Window Navigator using the add/remove section and it keeps giving me this error

"Cannot install 'avant-window-navigator'

This application conflicts with other installed software. To install 'avant-window-navigator' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict."

Can someone help me.

---

### Post by Catalyst2Death on 2008-08-27
You can go about this two ways, the gui and the command line. 

GUI:

System>Administration>Synaptic Package Manager

Then select "Search" and then type in avant-window navigator.  Follow the instructions to install. It will detect conflicts and help you remove them.
More on using synaptic package manager:
[http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html)

CLI:

Go to Applications>Accessories>Terminal
and then type:
```
$ sudo apt-get install avant-window-navigator
```

Again, it should tell you about conflicts and then prompt you about whether or not you want to remove the conflicting packages and install the ones required by avant-window-navigator.

Hopefully this helps

Good luck!


NOTE:  You will need to have compositing enabled to get this to work.  This may be non-trivial with and ATI video card, but you should be able to at least get it enabled by going to: System>Preferences>Appearance and then on the "Desktop effects" tab, select one of the three levels of effects, but make sure that they are not disabled.

---

### Post by SikEnCide on 2008-08-27
ok... i have that thing enabled im using compiz

---

