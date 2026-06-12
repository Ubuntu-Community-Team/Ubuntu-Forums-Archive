---
title: "xgl: numlock plus, minus, etc."
date: 2007-09-02
forum: Desktop Environments
---

### Post by felixnine on 2007-09-02
when i'm running xgl and numlock is on, the + - * / keys don't work. xev recognizes they keypresses when numlock is on, but the actual characters are only displayed when numlock is off. when numlock is off, of course, they numbers on the numpad don't work. this is oddly backward. i'd appreciate any help.

thanks,
andrew

---

### Post by vides2012 on 2007-10-27
I have the same problem, and it's really annoying.
Can anyone help us?

---

### Post by sloarch07 on 2007-10-28
I am also experiencing the same problem but I don't think I'm running xgl.

---

### Post by sloarch07 on 2007-11-04
I found a solution that worked for me.  Turns out I am running xgl, I just didn't realize it.  The problem I discovered was how my keyboard was configured in /etc/X11/xorg.conf.

_**The GUI method in Kubuntu**_

I am running Kubuntu so I first went to the Xkb options under  under: System Settings -> Regional & Language -> Keyboard Layout -> Xkb Options.  Under the Xkb Options dialog scroll down and find Keypad Layout Selection.  Then check the box for the keypad settings you want to use.  The two options are "Use keypad with unicode additions (arrows and math operators)" and "Force standard legacy keypad".  I found that the legacy keypad setting worked for me.  

**_The Manual Method_**

If you don't like using GUIs you can manually edited your /etc/X11/xorg.conf file.  *(Always make a backup copy first!)*  Open your xorg.conf file and locate the section for InputDevice.  Mine looks like this

```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" ""
EndSection
```

Add the XkbOptions to set your keypad options.  To use keypad with unicode additions (arrows and math operators) replace the line 

```
Option         "XkbOptions" ""
```

with:

```
Option         "XkbOptions" "setxkbmap -option keypad:oss"
```

and to force the standard legacy keypad"  replace the line
```
Option         "XkbOptions" ""
```

with:

```
Option         "XkbOptions" "setxkbmap -option keypad:legacy"
```
Hope this helps!

---

### Post by vides2012 on 2007-11-05
Thank You!
I tried the GUI method and worled for me!Though i had to configure regional settings to match my hungarian keyboard layout,but now it's perfect :)


edit.: well,well, now i can't use my alt gr key...:S

---

