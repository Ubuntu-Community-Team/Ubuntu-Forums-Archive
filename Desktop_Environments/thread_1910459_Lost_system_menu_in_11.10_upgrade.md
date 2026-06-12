---
title: "Lost system menu in 11.10 upgrade"
date: 2012-01-17
forum: Desktop Environments
---

### Post by brucehvn on 2012-01-17
I've upgraded to 11.10 with Unity and after many issues with nVidia drivers, I have it up and running, but I do not have the system menu in the upper right corner of the screen, which leaves me no way to shutdown, log off, restart, etc. other than going to a terminal to do it.

Please see the attached image. Somebody might suggest the menu icon might be off the right side of the screen, but the screen is fitting normally at the proper resolution and what we see here is the actual right side of the screen.

How can I get the system menu back?

---

### Post by Frogs Hair on 2012-01-17
Install the synaptic package manager from the software center and use it to locate and /or install the following packages .

```
gnome-power-manager
``` ```
indicator-power
```

If the indicator is not installed a restart using the button on the computer may be required before the indicator appears . If you find the packages installed , I don't know what the problem problem may be. 

I have seen a few threads indicating that some panel applet packages installed by default in a clean installation are not being installed in some upgrades .

---

### Post by Jamina1 on 2012-01-17
If you click on your name, you get you should see a menu with the various options.

---

### Post by Krytarik on 2012-01-17
Adding to *Frogs Hair*'s suggestions; I'd definitely also make sure the package "ubuntu-desktop" is installed, especially if this was a real *upgrade*, as opposed to a fresh installation.

Hope that helps.

---

### Post by brucehvn on 2012-01-17
I had forgotten to mention that this is the Unity desktop.

Frog's Hair:  I will try and install those packages and post the results.

Jamina1: Clicking on my name only gives me a "switch user" option, but none of the others.

---

### Post by xen423 on 2012-01-18
Under 'Dash Home' on Unity's panel search for 'Restart' and you can drop it into Unity's bar like I did.

---

### Post by brucehvn on 2012-01-19
Unfortunately, gnome-power-manager and indicator-power are already installed.

Any other suggestions?  What controls what shows up in the top panel when using the Unity desktop?

---

### Post by brucehvn on 2012-01-19
Problem solved.

Stumbled on the solution by doing another Google search, this time for missing shutdown menu instead of system menu.

Turns out just switching the theme from the default to Ambiance, than back, brings back the cog menu.

---

