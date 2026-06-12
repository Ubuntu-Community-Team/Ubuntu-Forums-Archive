---
title: "Make games play in a window"
date: 2007-12-25
forum: Gaming &amp; Leisure
---

### Post by Dwiman89 on 2007-12-25
HI, I have duel Monitors. I was wondering if there is a Way to get games that normally go full screen to play in a window? Because I have duel monitors And I run a game like Neverwinter Nights, It messes all up. The game menu is of so far to the right of the right screen i can even see it. Pleace help me to make it start in a window that can be minimized, maximized, and closed? thanks

---

### Post by cogadh on 2007-12-25
Many native games have the option of setting windowed mode in the graphics options, you should check to see if the games you are running have that option. 

As for NWN, I remember that in Windows you can edit the nwn.ini file, go to the [Display Options] section, change the entry "Fullscreen=1" to "Fullscreen=0" then add the line "AllowWindowedMode=1". I think that should still work in Linux, but I've never actually tried it myself.

BTW - This has always been a pet peeve of mine:
Duel -  A prearranged, formal combat between two persons, usually fought to settle a point of honor.
Dual -  Composed of two usually like or complementary parts; double
:)

---

### Post by Dwiman89 on 2007-12-25
Thanks, that did work. But the window cant be resized. It is huge.
```
[Display Options]
RefreshRate=0
BitsPerPixels=32
Height=600
Width=800
TexturePack=2
FullScreen=0
AllowWindowedMode=1

```
My whole resolution is 1200x3200. Can I add another line or at least edit it till it allows resize? I tried changing the width to 600,  but that didn't work.

---

### Post by Dwiman89 on 2007-12-26
here is waht it looks like...

---

### Post by Dwiman89 on 2007-12-26
OK this stinks SO bad. broke the sound in the game. i was screwing around and added AllowWindowResize=1 under the display section. it didnt work so I deleated the line and saved but the sound still doesnt work..PLEASE HELP!

---

