---
title: "E6400 Trackpad/Touchpad crazy"
date: 2011-11-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by moocan on 2011-11-15
Dear All,

I have installed Ubuntu 11.10 on Dell E6400 and Synaptics Touchpad/Trackpad is crazy.
I already have this on Ubuntu 11.04 but not so important.
I essentially use the trackpad.

clicking  on a menu .. menu open and close itself
clicking on Dash home ... Dash home appear and disappear
clicking on windows title bar ... window goes in full screen (as if I click two times)
using terminal ... moving cursor  over terminal window select text most of the time without clicking
using Firefox ... moving cursor over text always select text without clicking
using Firefox ... closing a tab always close two tabs
....

I have tried to slow down all mouse events under system settings but when I click the smiley most of the time one click equals two clicks.
There is as a "glue" effect with the cursor too.

Does any one know which settings could be modified to correct this 

Kind Regards

---

### Post by hellfire695 on 2011-11-15
what have you tried already to fix this problem?

I know I have a dell inspiron 1501 and correct me if im but i believe it too has a synaptic touchpad, does yours only do this when plugged in or all the time?

---

### Post by moocan on 2011-11-16
Hi,

Many thanks for your answer.

I found and tried this about xorg.conf and "AlpsPS/2 ALPS DualPoint TouchPad" device but I don't see really any difference.
[http://blog.khax.net/2009/02/08/adjusting-mouse-and-touchpad-speed-in-xorgconf/](http://blog.khax.net/2009/02/08/adjusting-mouse-and-touchpad-speed-in-xorgconf/)

I tried to install softwares add-ons in Ubuntu Software Center using touchpad as search but it the same thing.

It seems to be a little (just a little) better when computer is not plugged in (using battery).

I will update bios to last release and see if there is any difference.

Kind Regards

---

### Post by moocan on 2011-11-16
HI,

Performed BIOS update to the last one and .... no change.

If someone has information about it as it is very unusable/unstable.

edit: impacted device is the "DualPoint Stick"

Kind Regards

---

### Post by moocan on 2011-11-20
Hi,

Searching all around it seems there is a problem with the "DualPoint Stick" device.

As mentioned here there is already one year [http://ubuntuforums.org/showthread.php?t=1582745]("http://ubuntuforums.org/showthread.php?t=1582745") there is a sensitivity issue with the TrackPoint (which always select text or move objects) and the related left button (which always click two times).

Is there any solution to correct this ? or any tools ?

(This is not an hardware problem as it work well with Fedora 16.)

Kind Regards

---

