---
title: "ATI CC configuration"
date: 2010-03-17
forum: Desktop Environments
---

### Post by jus71n742 on 2010-03-17
I have had this issue with ATI for about 2 weeks now.  I am running 9.10 Server with a GUI (since its my main desktop so I can use all my RAM) I finally reinstalled after it flipped out the first time, it would lock up 2/3 screens and only allow full use of one screen.  And that would only happen with the desktop cube.  Now I have it back up and running correctly but now after a couple days I get this snowy looking screen (I attached it below).  The graphics cards are ATI 4850's (2 cards) .  Any one seen anything like this?  I get the log on screen just fine.  But when I log in the screen that has the log in splash is the attached screen ( and is the farthest right screen on my desk)
The middle screen will either be the same image as below or the background seen when the login is loading.  
I can also open things on those screens and when I log out I can see the actual desktops I am supposed to have (background taskbars etc)

I was just wondering if any one else has seen this before and knows a way to fix it.

Also the screens are no longer in order once logged in.  but the command 
```

sudo DISPLAY=:0 amdccle

``` 
won't bring up CCC on the correct monitor.

Setting Extra's to Normal brings everything back.  However I cannot move the monitors into the correct area
using the above command and then trying to apply anything will cause a segmentation fault and the program closes.

Does any one even know if CCC is even supported any more?  I read somewhere that 9.04 is supported but they lied lol.

---

