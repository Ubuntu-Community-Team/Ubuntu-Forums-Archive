---
title: "Desktop switcher not working in KDE"
date: 2009-11-13
forum: Desktop Environments
---

### Post by wrgb2 on 2009-11-13
I have the KDE desktop environment installed on a Xubuntu machine, and when I click on Dekstop 2 in the desktop switcher, it does nothing.  I looked in NVidia Xserver Settings and there is only one screen defined.  How can I define another one?

---

### Post by wrgb2 on 2009-11-14
Could someone help with this, please.  I have now installed Kubuntu to a dedicated partition.  In the Nvidia Xserver settings I see only a screen 0.  In the Dekstop Setttings, I have number of desktops set to 2, named Desktop 1 and Dekstop 2.  When I try to use the desktop chooser to select desktop 2, it just stays on desktop 1 - same applications minimized to the window list.  Does anyone know what I need to do to see the second desktop?

Thanks,

---

### Post by wrgb2 on 2009-11-15
Can someone help with this, please?

---

### Post by Zorael on 2009-11-15
There's some unfortunate naming collisions at work here.

[list][*]A "display" is a different X session (almost).
[*]A "screen" is a different monitor connected to the computer.
[*]A "desktop" is what you can switch with the Pager; several different desktops on the same screen in the same display.[/list]

So what you want to do is leave the Nvidia tool alone and head into System Settings -> Desktop -> Multiple Desktop, and set it to the number you want. You seem to already have done this.

Then you want to change the settings for the Task Manager (the list of running applications) and tell it to "Only show tasks from the current desktop".

---

### Post by wrgb2 on 2009-11-15
Thanks, Zorael, that took care of my problem and also cleared up some confusion about terminilogy.

---

