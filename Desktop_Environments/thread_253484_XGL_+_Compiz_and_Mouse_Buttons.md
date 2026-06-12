---
title: "XGL + Compiz and Mouse Buttons"
date: 2006-09-08
forum: Desktop Environments
---

### Post by jon3k on 2006-09-08
XGL and Compiz are running great on Dapper.  Old Duron 1.2 and a GeForce4 MX440.  Runs better than Windows XP could have ever hoped to run, I'm *VERY* happy with the performance.

I'm only having one problem, and it's with the mouse buttons after starting Compiz.  I have to use the middle button AND the left button to select things.  Basically left click is now middle mouse + left mouse button.

I changed Emulate 3 Button to false in my xorg.conf, but still having the problem.  Not a single error on a gdm restart, and the mouse works as expected before I start compiz.

Anyone ever run into this before?

---

### Post by jon3k on 2006-09-08
Relevent lines from xorg.conf
```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
EndSection

```

Relevent lines from Xorg.0.log
```

(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "false"
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)

```

---

### Post by jon3k on 2006-09-11
Bumping this back to the top - anyone have any idea on this?

---

### Post by Big_J on 2006-09-11
I don't know, try to use the graphical tool.. I'm on xp in college now so I'm not sure where it is, but it should be in the settings menu

---

### Post by jon3k on 2006-09-11
That was the first place I looked, unfortunately, I didn't see anything relevent.  Just switch left/right handed, pointers and motion options.  

Anyone know where the button configuration is stored?  I'm a lot happier editing configuration files than I am trying to deal w/ some graphical tool.

---

### Post by Big_J on 2006-09-12
Yeah I'd like to know that too, I've been trying to enable my side scroll for a while now!

---

### Post by jon3k on 2006-09-12
Anyone else have any idea on this one?  Seems like a simple enough question.  

Basically - where do you configure mouse buttons in Compiz?

---

### Post by PathSpace on 2006-09-12
You might have better success asking this on the Compiz forums:

compiz.net

---

### Post by jon3k on 2006-09-12
Thanks, I posted the same question on the Compiz.net forums, hopefully I'll get some feedback.  It's been a couple hours and nothing so far :(

I'm still digging around.  You'd think something as simple as configuring mouse buttons would be well documented.  It's definitely something with compiz because the mouse buttons work perfectly normal in Metacity.

---

### Post by cdaringe on 2008-01-18
did you ever solve this...a long time ago?
I'm still fightin it..

---

