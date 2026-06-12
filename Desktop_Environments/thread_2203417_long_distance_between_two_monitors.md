---
title: "long distance between two monitors"
date: 2014-02-03
forum: Desktop Environments
---

### Post by r.stiltskin on 2014-02-03
[Xubuntu 13.10, ASRock Z87 Extreme 4, Core i7-4770, using on-chip Intel HD graphics 4600.]

I'm working with 2 monitors, a Samsung 2433BW connected to my mobo's DVI port and a Vizio E241i-A1 (TV) connected to the HDMI-out port.

My complaint is that the mouse has to travel a long distance after the cursor leaves one monitor before it reappears on the other -- almost as far as if there's a third (invisible) monitor between them.

Other than this, the two displays are working nicely.  System settings shows the Samsung configured as 1920 x 1200, and the Vizio as 1920 x 1080.  These are the correct optimal resolutions according to the monitors' manuals & I haven't modified them.

Any ideas?

---

### Post by jp734 on 2014-02-03
What did you do to get the two monitors working?

---

### Post by r.stiltskin on 2014-02-03
Nothing elaborate.  After connecting the second monitor to the hdmi port I opened Settings Manager/Display.  At this point there were two entries in the display dialog: HDMI1 and HDMI3.  HDMI1 represents the original monitor connected to the motherboard's DVI port and HDMI3 is the new one connected to the motherboard's HDMI-out port (this was obvious because of the different resolutions listed for each one).  When you highlight each display there's a checkbox labeled "Use this output" and a list of drop-down menus to specify Position, Resolution, Refresh rate, Rotation and Reflection.  I changed only the "Position" fields, setting HDMI1 to "Right of" "HDMI3", and setting HDMI3 to "Left of" "HDMI1".

---

### Post by tgalati4 on 2014-02-03
Perhaps it expects HDMI2 so it leaves a placeholder.  Maybe you can remap HDMI3 to HDMI2.  What is the video driver that you are using for the Intel 4600?

Open a terminal and post the output of:

```
lspci
```

---

### Post by dargaud2 on 2014-02-04
If you play with the monitor positions in Settings Manager/Display, can you reverse the sides, put them on top of each others, etc ? If so you should be able to find an arrangement that suits you.

---

### Post by The Cog on 2014-02-04
You may find arandr easier to use - you can drag the screens around in there.
```
sudo apt-get install arandr
arandr
```

---

### Post by r.stiltskin on 2014-02-04
Thanks guys.

> **The Cog said:**
> You may find arandr easier to use - you can drag the screens around in there.
I'll keep that in mind in case I want to do anything more elaborate but it turned out not to be necessary in this case.

> **tgalati4 said:**
> Perhaps it expects HDMI2 so it leaves a placeholder.  Maybe you can remap HDMI3 to HDMI2.  What is the video driver that you are using for the Intel 4600?
Did you really mean lspci?  The video driver is i915 (shown by lsmod).
The video device reported by lspci is:
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
but what does that tell us?
Remapping the screens sounds interesting, but the solution turned out to be much simpler...

> **dargaud2 said:**
> If you play with the monitor positions in Settings Manager/Display, can you reverse the sides, put them on top of each others, etc ? If so you should be able to find an arrangement that suits you.
Well, the arrangement that I want is the left-right one I described yesterday.  But taking your suggestion I played with the settings and that turns out to be all that was needed -- after setting them to a top/bottom arrangement and then setting them back to left-right, now the cursor behaves properly.  Now as soon as it leaves one screen it reappears on the other.  So this question is "solved", even though the source of the problem remains a mystery.

A word of caution to anyone else playing with these settings.  They're pretty touchy, and so it's very easy to wind up with no usable display at all.  If this happens you can easily restore a default configuration just by deleting the .config/xfce4 directory and logging in again, but then you lose any customization you may have done to your panels, etc.   So I suggest that you always have a backup copy of your customized .config/xfce4 directory that you can restore if you get into trouble.

---

