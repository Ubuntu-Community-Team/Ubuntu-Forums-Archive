---
title: "how to change themes when you run on root mode"
date: 2011-02-04
forum: Desktop Environments
---

### Post by xsector on 2011-02-04
Hi,

I find it's annoying that when running nuatilus as root themes change into ugly default setting and also when you try to run package manager after entering password you got same issue

so after I test many things I got this and hopefully it's will work for you

first open terminal

run in super user mode

```
sudo -s
```

after entering the password you will be running as root

use this command 

```
gksu gnome-appearance-properties
```

all you need to install the themes or change the setting as you wish
noticed that boards and themes colours will not changed for nautilus if you run it as root  immediately and you need to reboot your computer to see the changes

this is my first post hopefully it's useful :mrgreen:

---

### Post by Frogs Hair on 2011-02-04
Nice ! added to links.

---

### Post by mcduck on 2011-02-05
First, you shouldn't be using "*sudo -s*" to start a root session. it doesn't load root's environment correctly, which may in some cases result in your normal user's files becoming owned by rot. Use "*sudo -i*" instead. Also since you are starting the *gnome-appearance-properties* with *gksudo*, the whole step if stating a root session beforehands is unnecessary. ;)

Anyway, there's a simpler solution to your problem. Applications running as root should already be using the same theme as you are using, assuming the theme you use is installed system-wide and not just for your own user account. In case you want apps running as root to use theme you have installed only for your own user, running following commands to link your theme directories into root's home will do the trick:
```

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

After that root has same themes available as your own user has, and is able to use the same theme even though it's only installed in your own user's home instead of /usr/share/themes.

---

### Post by VCoolio on 2011-02-05
Create the file /root/.gtkrc-2.0 and specify in there:```
gtk-theme-name="Clearlooks"
gtk-icon-theme-name="Faenza"
gtk-font-name="Verdana 8"
```
Like that. No need to reboot. Themes must be in /usr/share/themes or /usr/share/icons, or create symlinks like said above.

---

### Post by xsector on 2011-02-05
> **mcduck said:**
> First, you shouldn't be using "*sudo -s*" to start a root session. it doesn't load root's environment correctly, which may in some cases result in your normal user's files becoming owned by rot. Use "*sudo -i*" instead. Also since you are starting the *gnome-appearance-properties* with *gksudo*, the whole step if stating a root session beforehands is unnecessary. ;)

:
```

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```


thanx for reply and btw i already try these steps but it's doesn't seems to be working for me and I don't know why :confused:
using ubuntu since five years but am not expert user and thanx for sudo -i first time to know that :p

---

