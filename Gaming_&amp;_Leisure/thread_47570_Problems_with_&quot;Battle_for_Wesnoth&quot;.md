---
title: "Problems with &quot;Battle for Wesnoth&quot;"
date: 2005-07-09
forum: Gaming &amp; Leisure
---

### Post by Ferio on 2005-07-09
Hi, I've just installed the backported 0.9.1 version of "Battle for Wesnoth", a game I used to play when I used mostly my Windows system and that I would like to play in my Ubuntu, buy I've got a problem: after installing it, there's no entry in the Games menu, and if I try to run it from a terminal, I get this:

[i]Battle for Wesnoth v0.9.1
Started on Sat Jul  9 10:30:24 2005

started game: 4206327715
open /dev/sequencer: No such file or directory
Checking video mode: 1600x1200x16...
32
setting mode to 1600x1200x32
X Error of failed request:  BadValue (integer parameter out of range for operati on)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x48
  Serial number of failed request:  107
  Current serial number in output stream:  109

[/i]Could anybody help me, please? I have no idea about what the problem is.

---

### Post by t2kburl on 2005-07-09
I think 1280 x 1024 x32 is the highest res supported in wesnoth.
correct me if I'm wrong

is 1600x1200x32 the X res you use?

---

### Post by Ferio on 2005-07-10
Hmmm, the problem seems to be just the opposite, I'm using 1280 x 1024 and it doesn't work, but it does when using 1600 x 1200. Well, it's not a solution I like, but it's the solution, so... Thank you!

---

