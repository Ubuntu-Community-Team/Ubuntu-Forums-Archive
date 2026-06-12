---
title: "Please help me bring computer icon on desktop"
date: 2012-10-06
forum: Desktop Environments
---

### Post by Shrihari007 on 2012-10-06
hi i'm new to ubuntu.(installed it yesterday)as i'm from windows environment i noticed in ubuntu 12.04 i dont have any icon for computer thrash or network on desktop..please help me bring it.
(i've tried it in config editor but no use as there is no desktop option in apps-natutilus-)
ALSO tried typing in terminal: gsettings set org.gnome.desktop.background show-desktop-icons true
gsettings set org.gnome.nautilus.desktop computer-icon-visible true

---

### Post by JRV on 2012-10-06
The easiest way is to install ubuntu-tweaks.
Open a terminal and run the following commands:
```

sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

```
Run ubuntu-tweak, select Tweaks=>Desktop Icons

---

### Post by grahammechanical on 2012-10-06
Oh, yes you do!

The icons in the Launcher (left panel) are large and when there are a lot of icons in the Launcher the bottom icons folder up. I can just about see the icon of the waste paper basket at the bottom of the folded up icons.

Use the mouse to grab the Launcher (left click) and slide the launcher up. Then you will see the Rubbish bin icon.

You also have an icon for the Network Manager. It is one of our application indicators that are in the top panel on the right side. It looks like two arrows (one pointing up. The other pointing down). It tells me that you are connected to the router/hub by ethernet cable.

Click on that icon and you will see all available network connections. If you are connected by wireless then the icon will change to a cone of arcs radiating upwards.

Regards

P.S. May I suggest that as someone so new to Ubuntu that you read the Ubuntu Desktop Guide. Open the Dash by clicking the Ubuntu icon at the top of the Launcher and then type help in the search panel. Open the help documentation.

There is a saying in English: Walk before you can run. Gain more experience before trying out some of the suggestions on web sites.

P.P.S. You can reduce the size of the icons by going to the power/cog icon and selecting System Settings and then the Appearance uitility. At the bottom there may be a slider that lets you adjust the size of the icons.

If the slider is not there then you are using Ubuntu Unity 2D. Your computer may not be able to run Ubuntu Unity 3D. Open the Dash and type Additional Drivers. If you run that utility you may be able to activate a proprietary video driver that will let you have Ubuntu 3D and then you will see the slider in the Appearance uitility.

---

### Post by Shrihari007 on 2012-10-06
thanks..got it

---

