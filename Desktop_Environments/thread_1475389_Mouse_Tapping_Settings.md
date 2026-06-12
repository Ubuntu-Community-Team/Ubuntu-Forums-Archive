---
title: "Mouse Tapping Settings"
date: 2010-05-06
forum: Desktop Environments
---

### Post by bobbiscotti on 2010-05-06
In Kubuntu 10.04, there is an option in the mouse settings allowing for taps on corners of the trackpad to do functions such as right click, left click and middle click. These settings are found under System Settings> Keyboard & Mouse> Touchpad> Tapping

Is there any way to assign these to launch a program or run a specific command in this way? (run a command by tapping a corner of the pad, as seen as a service pre-installed for laptops in some windows installations)

---

### Post by Zorael on 2010-05-08
This would have to be an Input Action (under System Settings), but it doesn't seem like input actions can be triggered by mouseclick events. It may be that it's trivial to implement and that the developers only didn't know of a usecase that would warrant it. I suggest you make a feature request over at [KDE's bugtracker](http://bugs.kde.org).

To be a bit more technical, the Synaptics driver supports (configurable via xinput) click events at the top-right, bottom-right, top-left, and bottom-left corner, as well as taps with 1, 2 and 3 fingers (hardware permitting; old pads may have less functionality). For instance, I can tell my pad to interpret top-right taps as Button 12, which can be confirmed via xev. 12 seems to be the max, but it's high enough to be sure that it's not conflicting with anything else. So it would be very possible if only Input Actions could be bound to Button 12.

---

### Post by Zorael on 2010-05-08
It seems this is possible with **xbindkeys**.

As an experiment I set up top-right taps to be mouse button 12, and then told xbindkeys to start xterm when tapping there. So far it seems to be working, and it was pretty easy to set up.  Getting top-right taps to be button 12 was a bit more difficult, but not much.

> Description: Associate a combination of keys or mouse buttons with a shell command
 xbindkeys is a program that allows you to launch shell commands with
 your keyboard or your mouse under the X Window System.
 It links commands to keys or mouse buttons, using a configuration file.
 It's independent of the window manager and can capture all keyboard keys
 (ex: Power, Wake...).
 .
 It optionally supports a guile-based configuration file layout, which enables
 you to access all xbindkeys internals, so you can have key combinations,
 double clicks or timed double clicks take actions. Also all functions that work
 in guile will work for xbindkeys.
Homepage: [http://www.nongnu.org/xbindkeys/](http://www.nongnu.org/xbindkeys/)

Try the following, and just change values to fit whatever you had in mind. (If you want anything other than top-right corner taps, for instance.)

First install the **xbindkeys** package and have it create a default configuration file.
```
$ xbindkeys --defaults > ~/.xbindkeysrc
```
Then edit the **~/.xbindkeysrc** you just created in a normal text editor. Comment out the entries you don't want, and then create your own like this;
```
"*kate*"
  b:**12**
```
Replace *kate* with whatever command you want your corner-tap to run.

Then create a script to bind top-right corner taps to mouse button **12**, so it triggers the xbindkeys entry you just created (as per above).
```
#!/bin/bash

DEVICE="SynPS/2 Synaptics TouchPad"

echo "Setting top-right corner tap as mouse button 12"
xinput set-int-prop "$DEVICE" "Synaptics Tap Action" **[color="red"]8[/color] [color="deepskyblue"]12[/color] [COLOR="Orange"]0[/COLOR] [COLOR="Magenta"]0[/COLOR] [COLOR="Green"]0[/COLOR] [COLOR="Yellow"]1[/COLOR] [COLOR="Teal"]1[/COLOR] [COLOR="Sienna"]1[/COLOR]**

# Order of the digits for easy remembering: BYTES TR BR TL BL 1F 2F 3F
```
To explain the digits;
[list=1][*]the size of the property in bytes (**[color="red"]8[/color]**). Ignore that.
[*]**[color="deepskyblue"]top-right (TR)[/color]** tap behavior, here mouse button **[color="deepskyblue"]12[/color]**
[*]**[COLOR="Orange"]bottom-right (BR)[/COLOR]** tap behavior, here **[COLOR="Orange"]0[/color]** (feature unused)
[*]**[color="magenta"]top-left (TL)[/color]** tap behavior
[*]**[color="green"]bottom-left (BL)[/color]** tap behavior
[*]**[COLOR="Olive"]one-finger (1F)[/COLOR]** tap behavior, here mouse button **[color="olive"]1[/color]** (1 is left click; 2 is middle, 3 is right)
[*]**[color="teal"]two-finger (2F)[/color]** tap behavior, here set to behave as single-tap
[*]**[color="sienna"]three-finger (3F)[/color]** tap behavior, likewise[/list]

Save it as **~/.kde/Autostart/cornertap** and make it executable.
```
$ chmod +x ~/.kde/Autostart/cornertap
```
Run it from a terminal and see if it spouts any errors. Else, start up **xbindkeys** and see if it works.
```
$ ~/.kde/Autostart/cornertap
Setting top-right corner tap as mouse button 12
*<no errors here>*

$ xbindkeys
```
If everything works at this point, you'll just need to make sure xbindkeys also starts automatically.
```
$ ln -s /usr/bin/xbindkeys ~/.kde/Autostart/xbindkeys
```



As a reference, from #kde on irc.freenode.net;
```
[16:35] <Zorael> Do Input Action ignore mouseclick events by design or by technical limitation? I'm looking to bind a certain mouseclick to run a command, but the interface seems to ignore mouse events completely.
[16:35] <Sho_> I think it supports mouse gestures as triggers, but that's movements rather than clicks
[16:40] <Zorael> aw, shame. Feature request, perhaps
[16:41] <QwertyM> Zorael: but those actions are global, what if you somehow have to do something similar inside an app and this sort of combo interferes? :)
[16:41] <Zorael> QwertyM: But mouse button 12?
[16:42] <Zorael> Or Ctrl+Alt+middle click
[16:46] <Sho_> Zorael: xbindkeys comes in handy there
[16:47] <Sho_> (but yeah, would be nice if kde could do it)
[16:48] <Zorael> Sho_: I'll look into xbindkeys, thanks
[16:49] <Sho_> Zorael: it's a small tool to bind commands to be run to arbitrary button events. one can use it in combination with xdotool or xvkbd to send keyboard events to the active window, to bind keyboard shortcuts to mouse buttons. so mouse button event -> xbindkeys -> xdotool -> window.
[16:49] <Sho_> Zorael: I use that to for example have the tiltable wheel of my mouse switch tabs in apps via the standard next/prev tab shortcuts
```

Thanks go to Sho_.

---

