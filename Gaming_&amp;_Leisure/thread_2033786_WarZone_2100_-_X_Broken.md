---
title: "WarZone 2100 - X Broken?"
date: 2012-07-26
forum: Gaming &amp; Leisure
---

### Post by LongFist on 2012-07-26
(Ubuntu 12.04 LTS)
Does anybody know what this might mean?

[INDENT]>> warzone2100
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0xae
  Serial number of failed request:  427
  Current serial number in output stream:  429[/INDENT]

     ...I'm not sure what broke, or why, but lately I don't seem to be able to play WarZone2100 any longer.  It never really starts, it just leaves me the message above, and nothing happens.

     Is X broken, or is there another problem?

Thanks for your help,

The Lurking LongFist

---

### Post by thatguruguy on 2012-08-24
The error means the game is trying to run in a resolution that's not supported by your X server. You can try to run the game in a window, rather than full screen, to see if that helps.

---

### Post by LongFist on 2012-08-24
I'll *bet* this has something to do with the fact that 12.04 LTS doesn't "understand" my Intel i7's video system - it's the Intel on-chip variety, not the nVidia system everyone else appears to have purchased.

(Reason for this observation: Psychonauts runs horribly under Ubuntu 12.04 LTS --- but when I run the game under winDoze 7 it really flies, so it's obvious that I have something misconfigured on this machine...    ---I have both the Linux and winDoze versions of Psychonatus, so it's not a 'winDoze vs WINE' issue.)

Which is weird, because the game seemed to work earlier on.  I wonder what I changed to cause this condition?  (Come on, these things don't just break for no reason...)

Thanks for the heads-up --- at least now I know in which direction to look for a solution!

Thank you!  Thank you!  Thank you!

---

