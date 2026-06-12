---
title: "dual display"
date: 2009-10-17
forum: Desktop Environments
---

### Post by ultratek on 2009-10-17
need a program to configure dual display so i can tell which monitor to be the main desktop and the monitor on my left the extened???
thx=)

---

### Post by pytheas22 on 2009-10-18
Just go to System>Preferences>Display and you can configure all this.

---

### Post by wewantutopia on 2009-10-18
Either do what [pytheas22]("http://ubuntuforums.org/member.php?u=358340") said or if you have an Nvidia card goto 

System>Administration>Nvidia X Server Settings

Then X Server Display Configuration.

In the right pane, if on TwinView you can click on which monitor you want.  Check the box that says "make this the primary display for the X screen"  Then click the other monitor and in the Position drop down where you want that relative to the main display.

---

### Post by ultratek on 2009-10-18
with ati and even ubuntu's display options you cant pick make primary
for the sake of which monitor will be the main desktop...

ubuntu_64
ati raedon 4850 512
dell xps 420

---

### Post by pytheas22 on 2009-10-19
What do you mean by "main desktop" exactly?  You should just be able to choose to put your windows wherever you like.  If your screens are mirrored and you don't want that, you can uncheck that option in Ubuntu's display configuration.

---

### Post by ultratek on 2009-10-19
like have the menu bars that are at the top and bottom display on the right side without having to drag them over there...

---

### Post by pytheas22 on 2009-10-19
If you drag the panels over once, they should stay there after a reboot, but maybe they're not.  I think you can assign them to a specific screen by right-clicking the panel in an empty area and selecting properties.  You can also attach the panels to a particular screen in gconf; to do that, press alt-F2, type "gconf-editor" and navigate to the apps/panel keys.  I'm not sure exactly where to look, but somewhere in there should be an option for assigning the panel to a particular screen (screen 0 or 1).

---

