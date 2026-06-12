---
title: "problem with Xmodmap"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Skeletonix on 2006-09-11
**Hello ....**


My new mouse (Genius Ergo 525) work fine, but ... . One pair of buttons is defalt set to: *forward%Backward listing audio * (it's work in Rhythmbox). Yeah, that is good, but I wont set the buttons differently. I want setup them: Forward7Backward listing in Nautilus,firefox .... .

Here is  part of my default xmodmap:

```
   136
    137
    138
    139
    140
    141
    142
    143
    144         0x1008ff16 (XF86AudioPrev)
    145
    146
    147
    148
    149
    150
    151
    152
    153         0x1008ff17 (XF86AudioNext)
    154
  

```

By this I wanted changed Xmodmap:
```

sudo xmodmap -e "keycode 153 = XF86Back"
sudo xmodmap -e "keycode 144 = XF86Forward"

```

And this is result:

```
 142
    143
    144         0x1008ff27 (XF86Forward)
    145
    146
    147
    148
    149
    150
    151
    152
    153         0x1008ff26 (XF86Back)
    154
    155
    156         0x0000 (NoSymbol)       0xffe7 (Meta_L)
    157
    158

```

But if i try the buttons listing doesn't work! 

Pleas what I do wrogn ?

---

### Post by Skeletonix on 2006-09-11
Ups .. the buttons on mouse has same keycode as two multimedia buttons (for Audio back&for) on keybord ... Is possible setup keycode differntly on mouse and keybord ?

---

