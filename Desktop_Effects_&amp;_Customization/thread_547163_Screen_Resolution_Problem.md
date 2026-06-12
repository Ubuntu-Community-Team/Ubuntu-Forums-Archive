---
title: "Screen Resolution Problem?"
date: 2007-09-09
forum: Desktop Effects &amp; Customization
---

### Post by zutronius on 2007-09-09
Yesterday, Ubuntu was acting weird on me. I have always been running Ubuntu at a resolution of 1024x780. Yesterday it booted up at only 640x480, yet said in the Screen Resolution Window it was running at 1024x780. Today, the display worked fine until I logged into the main Ubuntu part and the display suddenly becomes very garbled and is unreadable.

Do I need to change the screen resolution in terminal? What is the problem? Can someone walk me through what to do?

---

### Post by w4ett on 2007-09-11
It's really hard to say exactly what the problem is......but lets start troubleshooting and get you back into your desktop. (You didn't mention what video card that you have, so we'll go the safe, generic route for now).  The fix may be as simple as reconfiguring your xorg.conf file.

From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Blue"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop.

---

