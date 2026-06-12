---
title: "macbook german keyboard"
date: 2009-06-10
forum: General Help
---

### Post by ringo999 on 2009-06-10
Hi folks,

just installed xubuntu jauntry and I'm having problems finding the correct settings for the german macbook keyboard to work correctly (ctrl key combinations, at symbol, f11 etc.). I've tried all kinds of model/layout settings with no success. On debian I had a manual entry in xorg.conf which made it work, but how are things handles on ubuntu? Anybody got it working? Thanks for any kind of help!

Peace
Ringo999

---

### Post by zvacet on 2009-06-10
It should be the same as in Debian.

---

### Post by ringo999 on 2009-06-11
still no success. :-( :-( :-(

here are some new findings:

in order to get F11/F12 to work from [https://help.ubuntu.com/community/MacBook4-1/Jaunty#Keyboard](https://help.ubuntu.com/community/MacBook4-1/Jaunty#Keyboard) :

> 
**Middle&Right Click with Left&Right Cmd Keys**

 After a fresh install of Intrepid (intrepid? This is a Jaunty document...), the middle mouse click is emulated on F11 and the right mouse click on F12. This has numerous disadvantages: 

[LIST]
[*]the fullscreen hotkey F11 for Firefox, F-Spot, etc. won't work
[*]the keys F11 and F12 are hard to reach, when using the trackpad
[*]the emulation service introduces a [bug]("https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/218263") with the CapsLock key: the LED won't work
[/LIST]
...

Uninstall the package **mouseemu**: 

sudo apt-get remove mouseemu

Reboot, to fix the broken keyboard.
from [https://help.ubuntu.com/community/AppleKeyboard#Corrections](https://help.ubuntu.com/community/AppleKeyboard#Corrections) :

> 
...

This section describe how to change the mapping of key to better match PC's keyboard. e.g.: Swap the Alt key and Command key. The idea is to make the keyboard work more like a normal PC keyboard. 
 
**Ubuntu 9.04 (Jaunty Jakalope)**

 Since Xmodmap have been replace by X Keyboard Extension, it's impossible to use Xmodmap to proceed with the mapping. Configuration can be done using the **Keyboard** preference tool

...
I tried all keyboard model/layout combinations for mac, so now what?

---

### Post by ringo999 on 2009-06-12
Ok I found a way to solve the problem:

Keyboard settings:
Model: Macbook/Macbook Pro
Layout: de

Then execute and put the following code into ~/.initrc

```
setxkbmap -option lv3:rwin_switch,apple:badmap
```I do not know why that extra code is necessary, I guess there is something wrong with the initial model/layout files. 

A bug? :?:

---

