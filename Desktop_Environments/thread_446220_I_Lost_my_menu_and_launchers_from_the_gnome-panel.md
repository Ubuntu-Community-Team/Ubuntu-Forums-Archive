---
title: "I Lost my menu and launchers from the gnome-panel"
date: 2007-05-16
forum: Desktop Environments
---

### Post by swaggoner on 2007-05-16
I am new to Ubuntu and have installed 7.04 on my laptop and I am using the standard gnome desktop -which has been working great for about a week. Today I was trying to get my Treo working and in the process lost my menu items and launchers from the gnome-panel. The panel is still there and the clock and network icons are still on the right, however, the Ubuntu Icon and menus are all gone from the left side. I have searched through the forum some and have made sure metacity is running and have even tried 'metacity --replace'. I have tried rebooting the system and still no icons. 

What I was doing when the problem occurred was trying the direction located:

([http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_configure_PalmOS_Devices](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_configure_PalmOS_Devices))

 How to configure PalmOS Devices

    * Read #General Notes 

```
gksudo gedit /etc/udev/rules.d/10-custom.rules

```
    * Insert the following line into the new file 

```
BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"
```

    * Save the edited file
    * Add the pilot-applet to the Taskbar by Right-Clicking on an empty spot
    * Follow the instructions on screen 

OK, seemed pretty straightforward. I created the 10-custom.rules file and added the entry. When I ran gksudo I got an error in the term window and later when I right-clicked on the panel bar up top to add the launcher - the new launcher appeared but all the others disappeared.

Any help would be greatly appreciated! Thanks.

---

### Post by zvacet on 2007-05-16
right click on panel>add to panel> scroll down and you will see main menu and tray icon.One of them(I realy don´t  remember wich one) will restore your launchers.

---

### Post by swaggoner on 2007-05-16
Thanks for the reply. I found where to add the menu items back in from your suggestion and got everything back now. I had to re-create the launcher shortcuts, but the menu was the big thing. Thanks.

---

