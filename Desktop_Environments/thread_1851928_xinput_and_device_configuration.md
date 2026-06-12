---
title: "xinput and device configuration"
date: 2011-09-29
forum: Desktop Environments
---

### Post by szpuni on 2011-09-29
Hello,

I have a small problem with xinput, well basically i can't find any proper documentation which could help me with it.

So going to the point I want to switch off device which is recognized by xinput as Power Button which is actually not a power button at all.

I have viewSonic View pad 10 which have 3 buttons. One is power button one which should show desktop (same as show desktop) and third one which should be working as enter key on keyboard.

Instead of having last key working as Enter it is switching off my wireless connection which is a bit annoying.

I can change this behavior by xinput and switch it off.
Problem is there is two power buttons in that list:
 >   &#8627; Power Button                                id=6    [slave  keyboard (3)]
   &#8627; Power Button                                id=7    [slave  keyboard (3)]

I can switch it of by issuing command:

```
xinput set-int-prop 6 "Device Enabled" 8 0
```

But problem is that ID is always changing every time you restart system and I want to have power button working and only second power button dissabled (one which is switching off my wireless connection)

I can do as well:
```
xinput set-int-prop "Power Button" "Device Enabled" 8 0
```

But this will match both buttons and disable them both.

Can somebody help me out how i can switch off one button or even change it so it will do something else than switching my wireless card off?

---

