---
title: "boot to command prompt"
date: 2008-03-28
forum: Desktop Effects &amp; Customization
---

### Post by binaryloc on 2008-03-28
The gnome and sfce window managers don't play nice with my display, I really need to just boot to a command prompt

---

### Post by pieisgood4589 on 2008-03-28
> **binaryloc said:**
> The gnome and sfce window managers don't play nice with my display, I really need to just boot to a command prompt

In the login window, instead of choosing "GNOME" under sessions in the bottom right-hand corner, I'm guessing that there's an option for "Terminal" but I'm not sure... You could always just bootup into GNOME then press CTRL+ALT+DELETE, (it's like the 3-finger salute in Windows, but the 3-finger terminal screen in Linux :))

---

### Post by Bliepo32 on 2008-03-28
Maybe try recovery mode? If that fails, try a live cd.

---

### Post by spupy on 2008-03-28
```
$ sudo apt-get install sysv-rc-conf
$ sudo sysv-rc-conf
```

With this program you can edit which services start when your Ubuntu boots. Find GDM and uncheck everything for it.

I got this tool from another thread. I don't use Ubuntu, but if I remember correctly, there is a graphical program that can do this, located in the "control panel" menu.

After you remove GDM from the starting programs, when  Ubuntu loads, you will be presented with a console awaiting login. After you login, type "startx" to start Gnome.

---

### Post by p_quarles on 2008-03-29
Easy one step command:
```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/D30gdm
```
To re-enable GDM, just the same command only the other way around:
```
sudo mv /etc/rc2.d/D30gdm /etc/rc2.d/S30gdm
```

---

