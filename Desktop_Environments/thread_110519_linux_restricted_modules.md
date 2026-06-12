---
title: "linux restricted modules"
date: 2005-12-31
forum: Desktop Environments
---

### Post by missmoondog on 2005-12-31
ok, on the very first machine of mine that i updated the kernel on, for some reason, i didn't allow it to install the linux restricted module, it is on my other 4 machines, although the version number of that is lower than the actual linux kernel number. do i really need it? can i remove it from the other 4 machines? anybody have any pointers in understanding exactly what that is?

thanks

---

### Post by Ampersand on 2005-12-31
The restricted modules contains the drivers for certain hardware (ATI and Nvidia graphics cards, and a few network cards). The list is given in the information about the package in Synaptic. If you type 
```
lsmod
```
in a terminal, you can see what modules are being used by your computer. If none of the restricted modules are being used, you can remove it.

---

### Post by missmoondog on 2005-12-31
cool.

thanks

---

### Post by az on 2005-12-31
If you are running without restricted modules, and do not have anything from multiverse, you are running a 100 percent free-libre software system!  W00t!

---

### Post by missmoondog on 2006-01-01
[QUOTE=Ampersand]The restricted modules contains the drivers for certain hardware (ATI and Nvidia graphics cards, and a few network cards). The list is given in the information about the package in Synaptic. If you type 
```
lsmod
```
in a terminal, you can see what modules are being used by your computer. If none of the restricted modules are being used, you can remove it.[/QUOTE]

the restricted modules for nvidia  are now installed and i've installed the glx package. i have a nvidia lanta card. i do beleive everything is working correctly, but i'm not seeing the nvidia splash screen like i do on my other system. something does pop up just before the login screen, but it's so fast i can't tell. i'm now looking into info for my kds visual sensation crt monitor, but of course, they have every monitor listed ever made, except this particular one on the kds site. my model number is just a plain vs-7. they have vs-7b and a few others, but no plain vs-7, so i can't find the screen settings to edit the necessary file i need to. i'm still stuck at 60mhz refresh rate as the only available setting.

---

