---
title: "Window title bar"
date: 2007-04-23
forum: Desktop Environments
---

### Post by deathkillspt on 2007-04-23
I've recently decided to give Ubuntu a try, i installed it once and it couldn't get my video driver working properly. So i instaled it again, this went on for about 4 hours or so. uninstalling and reinstalling about 6 times. 

Then i downloaded some envy thing that automatically installs the driver, it didn't work either so now for some odd reason i don't have window title bars. Like on Firefox i have no minimize, maximize, or close. and my video driver will not work at ALL. The max i can set my screen refresh rate is 54 I'm supposed to be able to put it around 75. can someone please help me with these 2 problems it will be greatly appreciated.

Here is a screen shot...
[http://img371.imageshack.us/img371/1750/screenshotrr1.png](http://img371.imageshack.us/img371/1750/screenshotrr1.png)

---

### Post by beerorkid on 2007-04-23
have you installed compiz or beryl?  This sometimes happens with beryl.

To get your window decorator back type this into a terminal ```
metacity --replace
```

What kind of video card do you have?

also which version of ubuntu?

If you have feisty you can install the restricted drivers.
system --> administration --> restricted drivers.

If you have an ATI of Nvidia card you can use [envy,]("http://www.albertomilone.com/nvidia_scripts1.html") it is quite good.

---

### Post by cherry316316 on 2008-04-03
> **beerorkid said:**
> have you installed compiz or beryl?  This sometimes happens with beryl.

To get your window decorator back type this into a terminal ```
metacity --replace
```


thanks,

oops, i figure out, when i restart the comp, the old settings return .
is there a permanent way to stop window decorator, coz it confuses
and slows the process of jumping from one window to another window
when multiple windows are open on desktop.

---

