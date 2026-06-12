---
title: "Colors off and insufficient range to adjust"
date: 2022-07-05
forum: Desktop Environments
---

### Post by ramcdona on 2022-07-05
I just updated to 22.04 (from 20.04).  Unfortunately, everything appears in a sad sepia tone.

Using the adjustment under 'Displays' 'Night Light', adjusting to the limit in the 'Less Warm' direction helps -- but the 'white' is still a dim sad tone.

Turning on maximum contrast through accessibility helps a bit -- but that certainly seems the wrong way to go.

How can I get white to show up as actual bright white?

Rob

---

### Post by Autodave on 2022-07-05
First off, let's make sure that it was the update that caused the problem.  Shut the machine down, disconnect your monitor cable at both ends.  Reconnect and try.  Also, do you have another monitor totry?

---

### Post by ramcdona on 2022-07-05
Thanks for the reply.

The monitor is fine and well connected.  This machine is set up dual-boot.  The Windows side is working as normal.

I suppose it could be the color calibration for the monitor -- I see how to turn it on/off (does that require a re-start or something).  Playing with the option quickly did not show any change.  I also saw no ability to adjust the monitor's calibration curves -- are those just hard coded somewhere?

Rob

---

### Post by ramcdona on 2022-07-07
I went back in and figured out how to change the active color profile.  Sadly, turning 'off' the color profile doesn't seem to actually do anything.  You actually have to choose another one and actively switch.

Anyway, switching to a random generic color profile 'fixed' the problem.  So, it seems that the problem is the default Dell 4320Q color profile is absolute junk.  That combined with a clunky interface for changing profiles -- and no obvious GUI for creating and tuning your own....

I found LPROF in the depths of the interweb -- but it seems abandoned at best.

---

