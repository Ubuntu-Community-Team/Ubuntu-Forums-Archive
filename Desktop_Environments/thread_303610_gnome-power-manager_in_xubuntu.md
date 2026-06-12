---
title: "gnome-power-manager in xubuntu"
date: 2006-11-20
forum: Desktop Environments
---

### Post by HydroDiOxide on 2006-11-20
I've installed the gnome-power-manager under xubuntu 6.10 because I couldn't find any decent powermanagement utillity under xubuntu. I've set it as an startup app, but it doens't seem to work (at least my screen is turned off after 3 minutes as I set through gnome-power-preferences).

Anyone any ideas on how to get the gnome-power manager to manage my power in Xubuntu?

---

### Post by jatatar on 2006-12-14
A simple and frustrating solution this is (hopefully!)
[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
Try one thing first

1. From terminal type gnome-power-preferences
    Select general tab -> select always show icon button -> close
    if it shows up yay, if not read on...

2. Execute from terminal gnome-power-preferences
    You should be able to see AC and BATT and General Tabs.
    If not you may need to load gnome-power-manager as a startup application
        A.  Add gnome-power-manager in autostarted apps. using startup command:
        gnome-power-manager
        browse under usr/bin if necessary
        B.  If its already there...good, if you had to add it logout/login and proceed to step 2.

3. Verify it is loaded by looking at XFCE4taskmanager
    Applications -> System -> Process Manager
        A.  It should be visible here somewhere, if not google for autostart command lines 

4.  Check that systray is on taskbar
    Right-click taskbar -> Add new item -> systray
    If you have it it will let you know...
    If not add to taskbar...repeat step one.  

Mine just needed the icon set to show...laptop was plugged in and charged.

Joe

---

