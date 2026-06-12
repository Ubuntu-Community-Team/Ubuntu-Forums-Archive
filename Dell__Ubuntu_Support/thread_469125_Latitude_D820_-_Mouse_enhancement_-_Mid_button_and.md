---
title: "Latitude D820 - Mouse enhancement - Mid button and wheel emulation"
date: 2007-06-09
forum: Dell  Ubuntu Support
---

### Post by mikeos on 2007-06-09
This post does not only concern Latitude D820, it should work on most laptops, PPCs and even desktops (though useless here).

The aim is to enhance mouse (glidepoint) features if you don't like, cannot, or just don't want to use external wheel-enabled mouse. D820 has two rows of mouse buttons, no middle button, no wheel. It has touchpad as well, but what if I don't want to use the touchpad and I'd like to scroll text using my glidepoint?

If you continue reading, you'll find out how to emulate middle mouse button (button 2) including wheel scrolling features with:

**Fn + SuperKey** (SuperKey is the third from the left bottom-most button on your keyboard with the W*****s logo)

The trick consists of emulation of the middle mouse button (button 2). That's the one which can be used for vertical scrolling as well. Let's go ahead:
 
1) First we say to linux kernel that some keyboard keys should be handled as mouse buttons. There's more ways to do it such as editing of the file */etc/sysctl.conf* and specifically *dev.mac_hid.mouse_** lines. However we'll use more elegant way for which you need:

**sudo apt-get install mouseemu**

and edit as root */etc/default/mouseemu* file. Try for example this command:

**sudo kate /etc/default/mouseemu**

and insert this line anywhere you like:

**MID_CLICK="-middle 0 126"   #  Map Fn+SuperKey to Button2**

Save.

Call: **sudo /etc/init.d/mouseemu restart**

2) Now we need to say to X Windows to emulate mouse wheel by adding few lines to the xorg.conf file. Do the following:

**sudo kate /etc/X11/xorg.conf**

One part of it should look something like this:

[I]Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
EndSection[/I]

Add the following lines right before the EndSection line:

[B]Option         "ZAxisMapping" "4 5"
    Option         "EmulateWheel" "on"
    Option         "EmulateWheelButton" "2"[/B]

Save.

Restart your X via CTRL+ALT+BACKSPACE and your're finished.

Be careful to always press FnKey a little bit sooner than the SuperKey, it means "almost simultaneously". While holding these two keys move your mouse and windows below your mouse pointer will do the same thing as if you used a mouse wheel. If additionally you push the CtrlKey, then e.g. web browsers should react by changing the font size.

Final note: no matter how easy it was, still I consider the solution unclean. In any case we violate the used keys to be strictly used for button emulation. If you have chosen to use LAlt instead of Fn+SuperKey, you would lose the possibility to use LAlt for switching between windows for example. The correct way would be to take kernel sources and enhance Andrew's idea ([http://lists.freedesktop.org/archives/xorg/2004-August/002404.html](http://lists.freedesktop.org/archives/xorg/2004-August/002404.html)) by another option such as "Emulate Button" which would allow us to make available the chosen keyboard key(s) not only for wheel emulation. Someone experienced here angry for C coding? :)

---

