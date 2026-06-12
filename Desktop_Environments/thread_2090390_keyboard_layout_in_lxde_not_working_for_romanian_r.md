---
title: "keyboard layout in lxde not working for romanian ro"
date: 2012-12-02
forum: Desktop Environments
---

### Post by doru001 on 2012-12-02
This is werid. In Precise under lxde after: 
```
setxkbmap -rules evdev -model pc104 -layout "us,cz,de" -option "grp:shift_caps_toggle"
```I can switch to Czech or German keyboard layouts, but after: 
```
setxkbmap -rules evdev -model pc104 -layout "us,ro" -option "grp:shift_caps_toggle"
```I can't switch to Romanian. The lxpanel indicator shows Romanian, but the layout is still us. 

In the login screen I can switch to Romanian and I can write in Romanian characters, but probably this comes from Gnome in Hardy in which I successfully installed the Romanian keyboard layout and from which I successfully updated first to Lucid and then to Precise. (all versions are LTS, *.04)

Now, what do you think about this?

---

### Post by doru001 on 2012-12-04
It is possible that the ro keyboard layout does not work in lxde *precisely* because I installed it successfully in Gnome, two releases before. 

How can I remove it from Gnome and login screen using text mode?

---

### Post by doru001 on 2012-12-05
Following these 
[http://linuxpixies.blogspot.ro/2011/09/quicktip-setting-keyboard-layout-in.html](http://linuxpixies.blogspot.ro/2011/09/quicktip-setting-keyboard-layout-in.html)
[http://askubuntu.com/questions/155424/changing-keyboard-layout-in-ubuntu-12-04-server-command-line-interface](http://askubuntu.com/questions/155424/changing-keyboard-layout-in-ubuntu-12-04-server-command-line-interface)
I did: 
```
gconftool-2 -s /desktop/gnome/peripherals/keyboard/kbd/layouts -t list --list-type string ["us  std"]
```The login screen still offered the ro keyboard layout. 

So I did this: 
```
sudo dpkg-reconfigure keyboard-configuration
```and I removed the ro keyboard layout from: 
```
/etc/default/keyboard
```The login screen still offered the ro keyboard layout. 

So I removed my lxde configuration: 
```
@setxkbmap -layout "us,ro"
```from: 
```
/etc/xdg/lxsession/LXDE/autostart

```The login screen still offered the ro keyboard layout. 

lxde still shows de correctly and ro as us.

---

### Post by doru001 on 2012-12-31
I succeeded to remove the Romanian keyboard layout from gnome and consequently from the login screen, but still it does not work in lxde. Maybe the character mapping is missing?

---

### Post by mariuz on 2013-01-27
> **doru001 said:**
> I succeeded to remove the Romanian keyboard layout from gnome and consequently from the login screen, but still it does not work in lxde. Maybe the character mapping is missing?


it works with "ro std" layout :p
I have made the tutorial here [http://www.lug-mures.org/2013/01/27/schimbare-tastatura-in-romana-maghiara-in-lxdelubuntu/](http://www.lug-mures.org/2013/01/27/schimbare-tastatura-in-romana-maghiara-in-lxdelubuntu/)

---

### Post by doru001 on 2013-01-31
> **mariuz said:**
> it works with "ro std" layout :p
I have made the tutorial here [http://www.lug-mures.org/2013/01/27/schimbare-tastatura-in-romana-maghiara-in-lxdelubuntu/](http://www.lug-mures.org/2013/01/27/schimbare-tastatura-in-romana-maghiara-in-lxdelubuntu/)
Thank you for your answer, but it did not work for me. Probably I need to learn more about characters and mapping in order to solve this.

---

