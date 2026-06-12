---
title: "mouse reconfigured with xinput jumps but only in games"
date: 2018-12-25
forum: Gaming &amp; Leisure
---

### Post by clarencepacelli on 2018-12-25
OS = Ubuntu 16.04.5 LTS

I recently bought a new mouse [(This one, if that helps)]("https://www.walmart.com/ip/BlackWeb-Wireless-Bluetooth-Touch-Mouse-75-ft-Range/936937537"), but found that it moved way too fast. I reconfigured it using ```
xinput set-prop pointer:"MOSART Semi. 2.4G Wireless Mouse" "Coordinate Transformation Matrix" 0.400000, 0.000000, 0.000000, 0.000000, 0.400000, 0.000000, 0.000000, 0.000000, 1.000000
``` but now I'm experiencing a rather strange issue.

Under normal use, the mouse works just fine, but the moment I try to play a first-person game (Minecraft for example), the camera starts jumping up and to the left. When I open an in-game menu the cursor appears in the center of the screen as expected, but the moment I move the mouse the cursor jumps to about 3/4 of the way between the upper-left corner of the screen and the center. I tried using xset to disable acceleration, but that only seems to affect my trackpad (which isn't experiencing the same issue as the mouse).

Any help is greatly appreciated!
[SIZE=1]Also, sorry if this is in the wrong forum. I posted here because the issue only happens in games.[/SIZE]

---

### Post by CatKiller on 2018-12-25
Why are you using a Coordinate Transformation Matrix? Yours won't change the speed, it will only restrict the pointer to part of the screen.

Something like ConstantDeceleration would be a much more sensible choice.

---

### Post by clarencepacelli on 2018-12-25
Thanks, that worked!

---

