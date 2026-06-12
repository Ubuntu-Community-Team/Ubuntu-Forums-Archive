---
title: "Dual monitor in lxde"
date: 2012-06-16
forum: Desktop Environments
---

### Post by ndonio on 2012-06-16
Hi all!

I have a samsung netbook (N150) with an Intel(R) Atom(TM) CPU N450 @ 1.66GHz (32 bit), 1 GB RAM and an Intel GMA graphic processor as graphic card. Since ubuntu 12.04 was too slow, as suggested [here]("http://ubuntuforums.org/showthread.php?t=1997932"), I installed lxde. But now I have a problem with the dual monitor in lxde: when I connect an external monitor it is cloned and I can't set them separately. I installed ARandR but it doesn't work.

Any suggestions?

Thanks!!

---

### Post by ndonio on 2012-06-16
By now I resolved in this way:

```
xrandr --output LVDS1 --mode 1024x600 --pos 0x0 --rotate normal --output VGA1 --mode 1920x1080 --pos 1024x0 --rotate normal
```

the external monitor is now an extension of the desktop. Now I'm trying to get the applet panel also in the second monitor: in this moment no panel is shown but if I maximize a window in the external monitor a stripe void space remains as if there is the applet panel.

Any suggestions??

Thanks!

---

### Post by ndonio on 2012-06-17
I resolved in this way:

I created two scripts in the .screenlayout/ directory with the help of ARandR:

```
~/.screenlayout$ cat single.sh 
#!/bin/sh
xrandr --output LVDS1 --mode 1024x600 --pos 0x0 --rotate normal --output VGA1 --off
lxpanelctl restart

~/.screenlayout$ cat dual.sh 
#!/bin/sh
xrandr --output LVDS1 --mode 1024x600 --pos 0x0 --rotate normal --output VGA1 --mode 1920x1080 --pos 1024x0 --rotate normal
lxpanelctl restart


```

adding the string "lxpanelctl restart" by hand (ARandR doesn't do it). Then, in the file
~/.config/openbox/lxde-ec.xml
I added the following lines between two </keybind> lines:

```

  </keybind>
  <keybind key="W-2">
  <action name="Execute">
  <command>sh ~/.screenlayout/dual.sh</command>
  </action>
  </keybind>
  <keybind key="W-1">
  <action name="Execute">
  <command>sh ~/.screenlayout/single.sh</command>
  </action>
</keybind>

```

so that using <super><1> and <super><2> I can switch between single and dual monitor configuration.

I hope this will be useful for others!

---

