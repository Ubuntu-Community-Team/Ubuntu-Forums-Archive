---
title: "How to turn off Xserver in the gui and turn it on in the command line"
date: 2007-04-04
forum: Desktop Environments
---

### Post by deadfred_10 on 2007-04-04
After this last xserver update I need to reinstall the newest Nvidia drivers and I have forgotten how to  turn off Xserver in the gui and turn it on in the command line.

if I use sudo /etc/init.d/gdm stop I can't get the command line to turn it back on or install the drivers.

TIA

---

### Post by martinw89 on 2007-04-04
Ctrl+Alt+Backspace closes X and "sudo /etc/init.d/gdm start" will start gdm in a terminal.  However, GDM will most likely restart X by itself.

---

### Post by phidia on 2007-04-04
I've used sudo init 1 (runlevels are different in ubuntu it seems) the nvidia installer will warn you about being in runlevel 1 but it worked for me.

Or you should be able to get another CLI by doing alt+ctrl+F1), F1-9
after using the gdm stop command.

---

### Post by brentoboy on 2007-04-04
from the GUI press

ctrl + alt + F1

that gives you a real terminal (as opposed to an x terminal)

then

```

sudo /etc/init.d/gdm stop

```

that kills the x running in the background

do your business and when you are done,

```

sudo /etc/init.d/gdm start

```

That'll get it going again.

if you sudo apt-get install nvidia-glx you get the same thing (except the drivers are a few months older than the ones that you get using envy or getting them from directly from nvidia and compiling, and they dont break when you update to a new kernel)

---

### Post by FuturePilot on 2007-04-04
Just log out and at the login screen press <Ctrl><Alt>F2 and you will be brought to the command line. Then once at the command line to start X just type ```
startx
```Or you can press <Ctrl><Alt>F7

---

