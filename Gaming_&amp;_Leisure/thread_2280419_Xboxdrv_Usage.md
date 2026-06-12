---
title: "Xboxdrv Usage"
date: 2015-05-30
forum: Gaming &amp; Leisure
---

### Post by Eslar on 2015-05-30
Hi All, 

I'm looking for some help with getting my Xbox controller to work on Ubuntu-
I have successfully installed and run Xboxdrv, and my controller is recognised and I can register input through it's listener and jstest-gtk.
However, no game I've attempted to use it in has successfully recognized it, and Steam had partial recognition in Big Picture mode with only some of the buttons working and none of them mapped correctly. 

I've trawled through all the information I could get my hands on, but it feels I am missing something here, perhaps some sort of wrapper for the input? 
Any help would be appreciated, 
Thanks
Eslar

---

### Post by efflandt on 2015-06-02
Did it not work with default Ubuntu gamepad support (which Ubuntu version)? I have not used xboxdrv, so not sure if it cooperates with default driver, or instead of default driver (whether anything else needs to be disabled).

As long as my Logitech F710 switch is set to xbox position it works by default in jstest-gtx, Steam Big Picture mode, and Steam games. With its switch in the other position (some sort of rumble controller), the controls are mixed up.

In Steam Big Picture mode can you get to Settings > Controller > Edit Controls?

In one game (Salvation Prophecy), which had a GUI for keyboard config, but not for gamepad (assumed xbox controller), the D-pad worked for menus, but not for spaceship weapon select/zoom. So I just pressed D-pad for assignment of some unused things in keyboard GUI config, then transferred those results from keyboard config xml file to gamepad config xml file for those functions. Although, I have not played that for awhile, so not sure if they made that easier to configure.

---

