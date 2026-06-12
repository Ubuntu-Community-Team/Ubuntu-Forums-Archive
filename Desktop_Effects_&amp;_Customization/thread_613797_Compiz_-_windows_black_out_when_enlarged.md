---
title: "Compiz - windows black out when enlarged"
date: 2007-11-15
forum: Desktop Effects &amp; Customization
---

### Post by d1ss0nant on 2007-11-15
Hello - I have the same issue as this fellow:

[http://ubuntuforums.org/showthread.php?t=550959](http://ubuntuforums.org/showthread.php?t=550959)

when using compiz, I often have my windows turn completely black until i resize them much smaller.  This does not happen when desktop effects are off.  Does anyone know of a way to correct this?  Thanks!

---

### Post by FuturePilot on 2007-11-15
I take it you have a Nvidia card. It's a bug in the driver. If you have an older card that is supported by the 96xx legacy driver, then you're kind of out of luck as of now. Nvidia improved the EXT_Texture_From_Pixmap out of memory handling in their latest driver and they have not yet added that fix to the 96xx driver due to the fact that the fix relies on some code that is specific to the newest driver and would involve some recoding of the 96xx driver. They are looking into this now to see if it would be possible to include the fix in the 96xx driver. 
There is one thing that you could try though, might help. Run Compiz like this.
```
compiz --replace --indirect-rendering --loose-binding
```

---

### Post by d1ss0nant on 2007-11-15
Thanks!  I will give it a shot.  For the record i have an nvidia geforce 4 440.  I'll post if it works once i try it out.

---

### Post by d1ss0nant on 2007-11-15
So i gave your solution a shot, and it worked for about a minute, then compiz began to have errors - windows would freeze,windows would turn grey (instead of black)...is there any other way?  Is there an error log i can post that would shed more insight into this problem?  I appreciate your help

---

### Post by d1ss0nant on 2007-11-21
This is still the most frustrating problem I have with ubuntu - does anyone have any additional info on this issue?  I am eagerly awaiting a fix.

---

