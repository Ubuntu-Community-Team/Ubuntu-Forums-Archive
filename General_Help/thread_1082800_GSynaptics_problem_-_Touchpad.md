---
title: "GSynaptics problem - Touchpad"
date: 2009-02-28
forum: General Help
---

### Post by MarkenK on 2009-02-28
Hello!
I'm a newbie at linux. My Dell Inspiron 1525's touchpad is rather vague. I hoped to improve that by downloading GSynaptics. I can't start the problem because it says, that i cave to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

I found xorg.conf at /etc/x11/ but there is no Synaptics section. I haven't found XF86Config at all.

here's the link for GSynaptics. It says pretty much the same thing: 
[http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)

I could really use some help with that, or if that's not at all the correct way to improve my touchpad, then any help on that.

Thanks in ahead!

---

### Post by leewebb on 2009-02-28
What it really means is to add it as an option to the input device settings (of /etc/X11/xorg.conf) which specifies the synaptics:

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig" "on"
EndSection

and reference it in the ServerLayout section using:

   Section "ServerLayout"
  #...
    InputDevice    "Synaptics Touchpad"
#...
EndSection

---

