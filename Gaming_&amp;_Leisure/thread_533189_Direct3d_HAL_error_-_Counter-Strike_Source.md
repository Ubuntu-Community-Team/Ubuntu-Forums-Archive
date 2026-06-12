---
title: "Direct3d HAL error - Counter-Strike Source"
date: 2007-08-23
forum: Gaming &amp; Leisure
---

### Post by Dev'olution on 2007-08-23
Hey guys,

Just installed steam..

However, i have a nvidia geforce go 7300 with the restricted drivers installed yet everytime i got to play counter-strike source i get crap graphics and get told my driver is out of date and have to use some Direct3d HAL one.

Help?

Kris

---

### Post by Dev'olution on 2007-08-23
bump... comeon guys.. a bit of help?

---

### Post by Dev'olution on 2007-08-23
Please help :(

---

### Post by angryfirelord on 2007-08-23
Patience my friend, an answer will come along (like this one) and please only bump threads if no one has responded within 24 hours.

When you use wine, remember to add the --enable-opengl flag at the end, otherwise you'll always have crappy graphics.

---

### Post by Dev'olution on 2007-08-23
Sadly, it did not work: 

Look at the following screenshot: :(

[http://img295.imageshack.us/img295/483/sadnessnw1.png](http://img295.imageshack.us/img295/483/sadnessnw1.png)

---

### Post by cogadh on 2007-08-24
It might be your driver. You are using the driver from the standard nvidia-glx package, try updating to the nvidia-glx-new package, it is actually the 9755 driver. I use that with my 7600 GS and I don't that error at all.

---

### Post by phissure on 2007-11-04
I am having the exact same problem.  I am using a restricted driver for my nVidia Quadro NVS 135M.  I am running Gutsy on a Dell Latitude D630.  If you need need more info on my system, please ask.

---

### Post by sirgogo on 2007-11-18
HELP!!!

I have the same error. Can someone please help!

---

### Post by Brynster on 2007-11-19
The simple answer is
the HAL message is because steam tries to discover your driver upon starting a game. It doesn't understand Wine, so it announces that HAL driver is out of date. HAL is not a driver its is short or Hardware Abstraction Layer, a middle bit between the equipment you have installed and Wine, which tells wine what you have installed and how best to use it.

You can simply tick the do not show this message again box and never be troubled by it again.

Now as far as graphic performance goes i would suggest setting all the in-game options to minimum, and tweek from there. You can also specify which version of DirectX you wish to emulate using the flag -dxlevel #0 (replace the # with 7, 8, 9) and see how that effects performance.

Also the real key is drivers make sure you have the latest drivers fro you graphics card installed


I hope this helps


Need any further help fel free to PM me

---

### Post by Rizado on 2007-11-20
> **Brynster said:**
> You can also specify which version of DirectX you wish to emulate using the flag -dxlevel #0 (replace the # with 7, 8, 9) and see how that effects performance.I think 81 is prefferable to 8.
So there are:

```
-dxlevel 70
-dxlevel 80
-dxlevel 81
-dxlevel 90
-dxlevel 95
```

Not sure about the 95 one though but I think I read it somewhere.

---

