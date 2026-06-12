---
title: "GSynaptic Touchpad Error"
date: 2009-04-28
forum: General Help
---

### Post by joeyknuccione on 2009-04-28
Trying to use GSynaptic Touchpad I get the following error:
> 
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

Here's my InputDevice from /etc/X11/xorg.conf:
> 
Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
    Option         "VertScrollDelta" "20"
    Option         "SHMConfig" "true"
EndSection

Any ideas?

Solved! 

Much, much thanks!

---

### Post by jtniehof on 2009-04-28
Jaunty doesn't use xorg.conf anymore. Take a look [here]("https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig") for directions.

---

### Post by Culip on 2009-07-18
> jtniehof

Thanks, your advice worked!

I'd had the same problem with my Panasonic Let'sNote (ToughBook Japanese version) W4 **since I'd upgraded to Ubuntu 9.04 Juanty.**
[COLOR="Gray"]
But now Gsynaptic Touchpad works. . . I can use wheel scrolling (because ToughBook has a circle touchpad, wheel scrolling is important for ToughBook users!) :D[/COLOR]

_**To those who have the same problem: **_

1. In a terminal type (for Gnome/Ubuntu):
```
gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi
```

2. Put this into the file and save it.
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>
```

---

