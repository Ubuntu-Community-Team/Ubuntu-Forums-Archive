---
title: "Screen resolution problems"
date: 2009-02-28
forum: General Help
---

### Post by AndyCooll on 2009-02-28
I have a new HP Advent laptop with a built in Intel GM45 graphics card.

For some reason when I log in it seems to detect two monitors (even though I only have the laptop screen itself), and these "two" monitors have different screen resolutions. So my desktop is set to 1440x900 but if I open Nautilus to full screen (for instance) it opens to the screen resolution of the other "monitor" which defaults to  1360x768. This is damn annoying!

To get round this I can run:
```
xrandr
xrandr --addmode HDMI-2 1440x900
xrandr --output HDMI-2 --mode 1440x900
```
And I can then "Mirror" the two screens.

However, I have to repeat this process each time I log in for the amendments to the settings are not stored.

Anyone have any ideas to help me solve this?

:cool:

---

### Post by dcstar on 2009-02-28
> **AndyCooll said:**
> I have a new HP Advent laptop with a built in Intel GM45 graphics card.

For some reason when I log in it seems to detect two monitors (even though I only have the laptop screen itself), and these "two" monitors have different screen resolutions. So my desktop is set to 1440x900 but if I open Nautilus to full screen (for instance) it opens to the screen resolution of the other "monitor" which defaults to  1360x768. This is damn annoying!

To get round this I can run:
```
xrandr
xrandr --addmode HDMI-2 1440x900
xrandr --output HDMI-2 --mode 1440x900
```
And I can then "Mirror" the two screens.

However, I have to repeat this process each time I log in for the amendments to the settings are not stored.

Anyone have any ideas to help me solve this?

:cool:

You can put those commands in your Sessions-Startup Programs (preferably inside a single script).

---

### Post by AndyCooll on 2009-03-20
Apologies for taking ages to reply. I've finally managed to fix the problem. While the commands I posted worked, they didn't provide a permanent fix.

Anyway, I'm not quite sure which of the following provided the actual fix since I applied both at the same time ...but one of the following worked!

```
sudo xrandr -s 1440x900
```

The other thing I did was go to System > Preferences > Screen Resolution. I moved the two monitors so they were side-by-side and then changed the resolution for the "unknown monitor" to "Off".

Now I have one monitor with the correct screen resolution when I log in.

:cool:

---

