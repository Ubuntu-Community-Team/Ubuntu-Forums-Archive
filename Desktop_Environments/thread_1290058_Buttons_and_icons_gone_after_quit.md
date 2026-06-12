---
title: "Buttons and icons gone after quit"
date: 2009-10-13
forum: Desktop Environments
---

### Post by audio_zoom on 2009-10-13
Hi 
when my pc boots it only displays a light blue desktop with no icons, task bar, and without right clicking.

I was able to bring up the file manager and the firefox with random key pressing (ctrl and alt + keys) but I want my standard gui back! I'm very new at this and before the last reboot I pressed the "quit" button in the top right corner of the screen. 

Xubuntu 9.04 installed today on a slow 500mhz intel pc.
Thanks for the help

---

### Post by wojox on 2009-10-13
Press Ctrl+Alt+F1 and run:

```
apt-get --reinstall install xubuntu-desktop
```

---

### Post by bagy on 2009-10-13
Try to run xfce window manager 
Alt+F2 and type xfwm4

---

### Post by audio_zoom on 2009-10-13
Thanks for your replies. The first one (re-install) didn't work. On to trying the second one

---

### Post by audio_zoom on 2009-10-13
Nope - running xfwm4 didn't help either.

---

### Post by mali2297 on 2009-10-13
Were you at least able to open the run dialog with Alt+F2? If so, use that to open a terminal window with the command
```

xterm

```
Then, in the terminal, try the commands
```

xfce4-panel
xfdesktop

```
That should get you the panel (task bar), icons and the right-click menu. If it doesn't work, report back any error messages shown in the terminal window.

---

### Post by audio_zoom on 2009-10-13
Thanks Martin - that worked, except when I ran it from the terminal window the panel disappeared as soon as I closed the terminal. So I just ran it from the run command. It'd be nice to know what it is that I did to make it happen, but it works and I'm happy.

Thanks everyone, problem solved.

---

