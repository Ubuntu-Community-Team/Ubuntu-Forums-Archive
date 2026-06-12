---
title: "How to configure a mouse with 3 buttons and a wheel?"
date: 2006-07-26
forum: Desktop Environments
---

### Post by Luffield on 2006-07-26
I've been using this mouse with Dapper for a while, but I re-installed last weekened and I can't get the 3rd button to work the way I want it. When I bought this mouse I edited xorg.conf to get the 3rd button to act as a middle button (like clicking on the wheel) but somehow I can't find how to do it now. The 3rd button is working as the left button atm.
Any advice on how to fix it? (and yes, I know, the best advice for next time is "backup your configuration files before you re-install! :D )
[This is the mouse]("http://www.logitech.com/index.cfm/products/details/IL/EN,CRID=2142,CONTENTID=8594"), if it helps.

---

### Post by Ziox on 2006-07-26
i can't tell you exactly what to do, but i suppose this might help...:

xev

and see which button # the computer see the middle button, then edit the xorg.conf file to match that number...i'll see if i can figure out more...

hopefully this helps

---

### Post by Luffield on 2006-07-27
Thanks Ziox, it does help -- turns out the 3rd button is button 8 (and buttons 6 and 7 don't exist). I'll try to edit xorg.conf accordingly when I have time.

---

### Post by GrinKestrel on 2007-12-14
How did you configure your xorg file? I've tried several different ways, and I haven't been able to get it to work right. Either it does nothing, or it mixes the buttons and scroll wheel up. I have a 5-button optical mouse, and the button setup is:


Left: Button 1
Right: Button 2
Center: Button 3
Alt_left: Button 4
Alt_Right: Button 5
Scroll Up: Button 6
Scroll Down: Button 7

Any info would be great.

---

