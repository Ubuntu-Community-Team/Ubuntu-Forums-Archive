---
title: "Mouse button assignments"
date: 2007-01-22
forum: Desktop Environments
---

### Post by brimbleshoes on 2007-01-22
I have looked all over.  I am just looking for a simple GUI config tool to map mouse buttons to certain functions -- something similar to the keyboard config tool.

My mouse buttons are all visible by xev.  

In ubuntu there is a keyboard shortcuts configuration -- is there a mouse button config tool also?

thanks in advance.

---

### Post by fabbaz on 2007-01-24
have the same problem.

---

### Post by conradcliff on 2007-01-24
same problem here as well...

---

### Post by teitunge on 2007-01-24
What mouse do you have, and is the plan to make the buttons to have the same functions as in windows?

---

### Post by brimbleshoes on 2007-01-25
ok...I fingered it out....

this was helpful:

[http://www.ubuntuforums.org/showthread.php?t=316441]("http://www.ubuntuforums.org/showthread.php?t=316441")

I wanted to use my extra mouse buttons for switching workspaces, so I did this (as an example):

Using xbindkeys and xautomation

First , get those packages via apt-get or Synaptic.

in a terminal type:

```
xev
```

move to the white box, then click on the buttons you want to assign and watch the terminal for their numbers.

Then create an xbindkeys config file in your /home/[username] directory:


```
.xbindkeysrc
```

then enter something like this text in that file (mine happened to be buttons 8 (thumb) and 2 (wheel)):
```
"/usr/bin/xte 'keydown Control_L' 'keydown Alt_L' 'key Right' 'keyup Control_L' 'keyup Alt_L' &"
b:2 + Release

"/usr/bin/xte 'keydown Control_L' 'keydown Alt_L' 'key Left' 'keyup Control_L' 'keyup Alt_L' &"
b:8 + Release
```

Note that 'xte' is being used to capture the X events (part of the 'xautomation' package), and that the arguments given to 'xte' are the key assignments made in the 'Keyboard Shortcuts' (System --> Preferences --> Keyboard Shortcuts) for switching right and left among the workspaces.  See the 'xte --help' for keyboard and mouse-button naming.

Then start up xbindkeys:

```
xbindkeys -n -v
```

The above will start it in a non-daemon mode for testing.  Make sure no errors occur and then use your new shortcuts (on my mouse in my case) and the events will show up in the console.  Then when you're confident that everything is cool -- in the terminal just type:

```
xbindkeys
```

If you want to have it startup on login -- you should be able to add the xbindkeys to a startup script -- I haven't done that yet.  

So this is a piggy-back solution based on the keyboard shortcut -- but its the best I could come up with.  I'm sure there is a better way, but I was using tricks from my Windows 'AutoHotKey' (autohotkey) days.

feel free to comment, or let me know if you have issues.

-- Tom

---

### Post by Hasen_A on 2007-02-02
I am trying to get the minimize and maximize funktion to work using the following code. alt + f9 is implemtend and works on keyboard and when i put b:2 instead of b:4 it works. b:4 is my mouse scrolling up, which doesn't work for some reason. xev detects scroll up as button 4.



```
"/usr/bin/xte 'keydown Alt_L' 'key F9' 'keyup Alt_L' &"
b:4 + Alt
```

further when i try to use button 8 xev spits out this:

> KeyPress event, serial 29, synthetic NO, window 0x4200001,
    root 0x76, subw 0x0, time 2220895245, (155,172), root:(160,220),
    state 0x18, keycode 100 (keysym 0xff51, Left), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


thanks in advance
andy

---

### Post by brimbleshoes on 2007-02-12
So what exactly is the issue?

USUALLY the buttons are:

Button 1 - left button
Button 2 - scroll wheel button (middle button)
Button 3 - right button
Button 4 - scroll up
Button 5 - scroll down
Button 8 - [nothing]

Do you want minimize as the scroll button or the scroll up button?


> 
further when i try to use button 8 xev spits out this:

Quote:
KeyPress event, serial 29, synthetic NO, window 0x4200001,
root 0x76, subw 0x0, time 2220895245, (155,172), root160,220),
state 0x18, keycode 100 (keysym 0xff51, Left), same_screen YES,
XLookupString gives 0 bytes:
XmbLookupString gives 0 bytes:
XFilterEvent returns: False


its possible button 8 is already assigned somewhere -- or xev can't see it properly because xorg.conf isn't configured for an 8 button mouse.  

here is what my section for my mouse looks like in my xorg.conf 

> 
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
        Option      "Buttons" "8"
EndSection


My mouse brand is a Micro Innovations (IBM branded) mouse.  Physically it only has 6 buttons -- but the thumb button shows up in xev as button 8.

---

