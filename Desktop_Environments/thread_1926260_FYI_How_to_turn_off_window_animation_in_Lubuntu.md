---
title: "FYI How to turn off window animation in Lubuntu"
date: 2012-02-16
forum: Desktop Environments
---

### Post by marinara on 2012-02-16
Here's a how to, how to turn off [window animation]("http://openbox.org/wiki/Help:Upgrading_to_3.4#Animated_iconify_and_restore") in Lubuntu

you have to change the openbox config file:
go to terminal and type 
[COLOR=#d3d3d3]sudo leafpad ~/.config/openbox/lubuntu-rc.xml[/COLOR]
look for this xml
<animateIconify>yes</animateIconify>
change it to this xml
<animateIconify>no</animateIconify>

Enjoy!

---

