---
title: "How to set panel(s) on a specified screen in CLI ?"
date: 2014-08-13
forum: Desktop Environments
---

### Post by ponsfrilus on 2014-08-13
Hi all,
   I'm looking for a way to move my panel on a specfied screen in command line interface. I'm using xubuntu (xfce 4.10). 

I've tried ```
    xfconf-query -c xfce4-panel -p /panels/panel-0/output-name -s LVDS1
    xfconf-query -c xfce4-panel -p /panels/panel-1/output-name -s LVDS1
``` but it doesn't work. I'm probably missing something.

Thanks !

EDIT: SOLVED ! Thank to Toz. Use **xfce4-panel -r** to refresh the panels.

---

### Post by Toz on 2014-08-13
It should work. Do you have the panel numbers and displays correct? 

What do the following commands return?
```
xfconf-query -c xfce4-panel -p /panels -lv
```
...and:
```
xrandr -q | grep " connected"
```

---

### Post by ponsfrilus on 2014-08-13
Hi Toz,

$ xfconf-query -c xfce4-panel -p /panels -lv
```

/panels                           2
/panels/panel-0/autohide          false
/panels/panel-0/background-alpha  100
/panels/panel-0/background-style  0
/panels/panel-0/enter-opacity     100
/panels/panel-0/leave-opacity     100
/panels/panel-0/length            100
/panels/panel-0/length-adjust     true
/panels/panel-0/mode              0
/panels/panel-0/output-name       LVDS1
/panels/panel-0/plugin-ids        <<UNSUPPORTED>>
/panels/panel-0/position          p=6;x=0;y=0
/panels/panel-0/position-locked   true
/panels/panel-0/size              21
/panels/panel-0/span-monitors     false
/panels/panel-1/autohide          true
/panels/panel-1/background-alpha  15
/panels/panel-1/disable-struts    false
/panels/panel-1/enter-opacity     100
/panels/panel-1/leave-opacity     100
/panels/panel-1/length            100
/panels/panel-1/length-adjust     true
/panels/panel-1/mode              0
/panels/panel-1/output-name       LVDS1
/panels/panel-1/plugin-ids        <<UNSUPPORTED>>
/panels/panel-1/position          p=8;x=960;y=1176
/panels/panel-1/position-locked   true
/panels/panel-1/size              25
/panels/panel-1/span-monitors     false

```

$ xrandr -q | grep " connected"
```
LVDS1 connected 1600x900+1680+150 (normal left inverted right x axis y axis) 309mm x 174mm
HDMI1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 433mm x 270mm
```

Actually the xfconf-query says LVDS1 but the panels are on HDMI1. In the Panel tool in settings, output is set on automatic for both (but if I change in settings to LDVS1 for both panel it work correctly).

Any idea ?

---

### Post by Toz on 2014-08-13
What happens if you restart xfce4-panel:
```
xfce4-panel -r
```

Does anything change? Can you post back again the results of those 2 commands above after the panel restart?

---

### Post by ponsfrilus on 2014-08-13
> **Toz said:**
> What happens if you restart xfce4-panel:
```
xfce4-panel -r
```

Does anything change? Can you post back again the results of those 2 commands above after the panel restart?

Oh Toz **thank you**, that was what I was missing !

$ xfconf-query -c xfce4-panel -p /panels -lv
```
/panels                           2
/panels/panel-0/autohide          false
/panels/panel-0/background-alpha  100
/panels/panel-0/background-style  0
/panels/panel-0/enter-opacity     100
/panels/panel-0/leave-opacity     100
/panels/panel-0/length            100
/panels/panel-0/length-adjust     true
/panels/panel-0/mode              0
/panels/panel-0/output-name       LVDS1
/panels/panel-0/plugin-ids        <<UNSUPPORTED>>
/panels/panel-0/position          p=6;x=0;y=0
/panels/panel-0/position-locked   true
/panels/panel-0/size              21
/panels/panel-0/span-monitors     false
/panels/panel-1/autohide          true
/panels/panel-1/background-alpha  15
/panels/panel-1/disable-struts    false
/panels/panel-1/enter-opacity     100
/panels/panel-1/leave-opacity     100
/panels/panel-1/length            100
/panels/panel-1/length-adjust     true
/panels/panel-1/mode              0
/panels/panel-1/output-name       LVDS1
/panels/panel-1/plugin-ids        <<UNSUPPORTED>>
/panels/panel-1/position          p=8;x=960;y=1176
/panels/panel-1/position-locked   true
/panels/panel-1/size              25
/panels/panel-1/span-monitors     false
```

$ xrandr -q | grep " connected"
```
LVDS1 connected 1600x900+1680+150 (normal left inverted right x axis y axis) 309mm x 174mm
HDMI1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 433mm x 270mm
```


Yay yay yay :-) Thanks again!

---

