---
title: "Help getting mouse thumb buttons to act like alt key"
date: 2006-10-06
forum: Desktop Environments
---

### Post by tlwolf on 2006-10-06
What I want to do is have my mouse thumb buttons act like the alt and control keys, mainly for World of Warcraft. I've been able to get my mouse buttons working with Firefox, Thunderbird, and a few other programs using imwheel. I can also get imwheel to press alt however the button gets released right away. Because I'm using it as a modifier it a problem. 

So I looked into if imwheel had any extra options. It turned out they did, I can set the time for how long before it releases the buttons. I guess this would work but not exactly what I'm looking for. 

Next I looked into xmacro. This would mostly do what I want but I would have to hit my thumb button to press alt and push it again to release alt, much like the caps lock key. I think this is better but defiantly not what I'm going for.

So I'm wondering if theres is some way of making mouse buttons act like modifier buttons.

BTW My mouse is a Microsoft Wireless Laser Mouse 6000 and my keyboard is a Microsoft Wireless Comfort Keyboard.

I'm using the default mouse drivers. I tried evdev as the drivers but when I scrolled fast it pressed diffrent buttons. The thumb buttons are currently buttons 8 and 9.

This is my imwheelrc file
```
"^Firefox-bin$"
None,Thumb1,Control_L|w
None,Thumb2,Alt_L|Left
"^Mozilla-thunderbird-bin$"
None,Thumb1,M|-M
None,Thumb2,Delete|-Delete
"^Wine$"
None,Thumb1,Alt_L
None,Thumb2,Control_L
".*"
```

If theres any more info needed just say so.:)


Spencer

---

