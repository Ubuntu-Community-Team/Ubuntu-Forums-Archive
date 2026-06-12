---
title: "Make horizontal mouse wheel faster?"
date: 2009-01-19
forum: General Help
---

### Post by crazyfuturamanoob on 2009-01-19
I got a mouse, with 4-directional mouse wheel (it can move sideways too, you know).

But when a vertical click moves up/down 3-4 rows, horizontal moves barely 1 character left/right.

I want horizontal click to move at least 20 characters! How can I change it?


Is this is program-specific? If so, I'm not going to edit all programs' settings.

Firefox, SciTe and gedit are good for me, I don't care about the rest.

---

### Post by crazyfuturamanoob on 2009-01-29
bump

---

### Post by crazyfuturamanoob on 2009-01-31
anybody?

---

### Post by ianhaycox on 2009-01-31
Could try this in xorg.conf

[http://ubuntuforums.org/showpost.php?p=3951507&postcount=6](http://ubuntuforums.org/showpost.php?p=3951507&postcount=6)

changing Vert to Horz ?

E.g.

Option "HorzScrollDelta" "6"

or Horiz or Horizontal ?? 

If it works let us know.

---

### Post by crazyfuturamanoob on 2009-01-31
But there's no section for mouse or keyboard! Huh? 

I have a mouse and keyboard, and I'm using them as I type this message.

They work correctly. Should I create it?

---

### Post by ianhaycox on 2009-01-31
You could try,

Firstly make a backup of your original /etc/X11/xorg.conf then read through the whole thread [http://ubuntuforums.org/showthread.php?t=628725&page=1](http://ubuntuforums.org/showthread.php?t=628725&page=1) and try pasting in an InputSection without your changes to make sure it works.

Change one thing at a time, restart X and check it works, e.g. change VertScroll... from 3 to 6 to 9 etc. and see if it has an effect. Then try the horizontal changes.

If your feeling really adventurous you could look through the X server source and find the bit that deals with VertScrollDelta and see if there is anything around it that might work for you.

I haven't got a horizontal scroll wheel, so I'm afraid you are on your own unless someone else can advise.

---

### Post by crazyfuturamanoob on 2009-01-31
I copy-pasted this into my xorg.conf:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "VertScrollDelta"       "6"
EndSection

```
Restarted X, ctrl+alt+backspace, and didn't work. :(

---

### Post by ianhaycox on 2009-02-01
You most probably need a ServerLayout section as well to tie together all the device, monitor and inputdevice sections.

It's a long shot but try creating very basic xorg.conf with all the necessary sections.

Running,

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

might create a starting xorg.conf for you, but as usual back up what works first.

---

