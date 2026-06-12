---
title: "Restore Original LightDM Greeter"
date: 2014-12-02
forum: Desktop Environments
---

### Post by ahmedm2 on 2014-12-02
[COLOR=#333333][FONT=UbuntuRegular]When I login to ubuntu, I get a menu in the top right corner to load an Ubuntu environment.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]This means that the lightdm greeter is corrupt. I tried to locate the lightdm.conf but I can't find it and read some where it's deprecated. I downloaded the original lightdm package and replaced every file in vain[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]All I need is to restore it where I have 2 users with different backgrounds + Guest + No Grid.

Note: When computer is locked, the LightDM Greeter is working normally.


[/FONT][/COLOR]

---

### Post by ahmedm2 on 2014-12-03
Any ideas?

---

### Post by kansasnoob on 2014-12-04
It sounds like you may have installed 'lightdm-gtk-greeter' - perhaps as a dependency of another desktop environment like Lubuntu or Xubuntu???

If that's the case you may be able to just purge 'lightdm-gtk-greeter' and then reinstall and reconfigure 'lightdm' and the 'unity-greeter', but I'd use the "-s" tag to "simulate" what is going to be removed if you purge 'lightdm-gtk-greeter' just in case it wants to remove something you prefer to keep:

```
sudo apt-get purge -s lightdm-gtk-greeter
```

If that looks OK **(if in doubt post the full output here)** then drop the -s:

```
sudo apt-get purge lightdm-gtk-greeter
```

Then reinstall 'lightdm' and the 'unity-greeter':

```
sudo apt-get install lightdm unity-greeter
```

Then reconfigure 'lightdm':

```
sudo dpkg-reconfigure lightdm
```

Hopefully that works.

---

