---
title: "Enabling nvidia"
date: 2007-03-03
forum: Desktop Environments
---

### Post by JML22 on 2007-03-03
i'm trying to install beryl with xgl
but i can't get past this step
$ glxinfo | grep direct

in a terminal. If it returns

direct rendering: Yes

I put in that first command and dont get that output

also when i open up my xconfig its blank
I have ran envy script and it says its already installed

I have a compal Hel80 with a 7600 go nvidia card
does anyone know what i'm doing wrong?

---

### Post by kerry_s on 2007-03-03
Did you install the nvidia drivers?
sudo apt-get install linux-restricted-modules-generic  nvidia-glx
sudo nvidia-xconfig
reboot

---

### Post by Dylnuge on 2007-03-03
Jumping ahead of the game. First you need to know whether to use Generic or not. Depends on the arch you installed Ubuntu for. You can find this when the system boots up-it should its loading kernel 2.6.17.11-generic or 2.6.17.11-386 or something like that. Just know that last part.

---

### Post by JML22 on 2007-03-03
yeah i have
they're installed
even when i bring up the config file its blank
is that right?

---

### Post by kerry_s on 2007-03-03
Your probably looking at the wrong file.
gedit /etc/X11/xorg.conf

---

### Post by JML22 on 2007-03-03
Generic

No i run that command and it comes up blank
i've read hours on this, which is why i've come to the forums finally

---

### Post by rsambuca on 2007-03-03
In linux the file and directory names are case sensitive.  Try copying and pasting the command in a terminal```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by JML22 on 2007-03-03
oh capital X?
i'll try that when i get back to my linux comp

that might be it

---

### Post by rsambuca on 2007-03-03
I think I spent about 2 hours playing around with that when I first started.  It really ticked me off that I could copy and paste a command and it worked, but for some reason when I typed it - nada.

---

