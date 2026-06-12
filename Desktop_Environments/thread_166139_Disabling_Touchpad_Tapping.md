---
title: "Disabling Touchpad Tapping"
date: 2006-04-25
forum: Desktop Environments
---

### Post by KyjL on 2006-04-25
Yes, I've searched the forums OVER AND OVER about this, and tried an awful lot. gsynaptics/qsynaptics doesn't so much of anything and editing xorg.conf doesn't do anything either (MaxTapMove=0 or... whatever).

Seriously getting annoyed at this D:<

PS: Apparently messing around with those three things also disabled my trackpad (I use an IBM R51 Lappytop). Weird.

---

### Post by taylork on 2006-04-26
Did you play around with the synclient command as described here?:

[http://voidmain.is-a-geek.net/redhat/fedora_1_synaptics_touchpad.html](http://voidmain.is-a-geek.net/redhat/fedora_1_synaptics_touchpad.html)

doing a 

synclient MaxTapTime=0

turns tapping right off for me.

You can also resort to not using the synaptics guy by taking it out of the Server Layout section all together as this will get rid of the tap.

---

