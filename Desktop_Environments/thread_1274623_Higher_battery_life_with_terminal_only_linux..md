---
title: "Higher battery life with terminal only linux."
date: 2009-09-24
forum: Desktop Environments
---

### Post by ashour on 2009-09-24
Hello,

I want to use a laptop only to do basic tasks that could be easily achieved from within the terminal but the main goal is to have linux last as long as possible, would the termination of X Windows (GDM Or KDE) and only using terminal helps?

I think that would be like using a 16 bit OS thats not supposed to consume much power?

would that work?

if it will how could i achieve it i mean to make my linux only loads terminal and boots into it?

thanks

---

### Post by scragar on 2009-09-24
The easiest way is to open your grub boot list and add 3 to the end of the kernel line to stop your boot at the command line rather than gui.
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Lars Noodén on 2009-09-25
Dimming or turning off the backlight on the screen would probably have the largest increase on your battery time.  I wouldn't worry as much about X as I would about eye candy and cruft.  FVWM-Crystal or Openbox would be better choices then for the desktop.  

There might also be a way to scale back CPU activity:

[http://www.ibm.com/developerworks/linux/library/l-cpufreq-1/](http://www.ibm.com/developerworks/linux/library/l-cpufreq-1/)

---

