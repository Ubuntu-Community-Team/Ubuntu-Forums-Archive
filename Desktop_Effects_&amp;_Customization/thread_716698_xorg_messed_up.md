---
title: "xorg messed up"
date: 2008-03-06
forum: Desktop Effects &amp; Customization
---

### Post by denbeiren on 2008-03-06
After changing from a 19" lcd to a 22" lcd, i can't change the resolution to one that i like. 
The new screen supports different resolutions that the old screen didn't. 

As a result of that, i am not able to change the desktopresolution to my liking. 

I renamed my xorg.conf to xorg.conf.back and rebooted, thinking that this would solve the problem which it didn't.

Could someone help me out in getting an xorg.conf that supports my monitor?

Link to the specs of my monitor : 

[http://www.agneovo.com/nl/products/h-w22.htm](http://www.agneovo.com/nl/products/h-w22.htm)

Thanks in advance,.. Bert

---

### Post by FuturePilot on 2008-03-06
What graphics card do you have and did you install a driver for it?

---

### Post by scrooge_74 on 2008-03-06
did you try sudo dpkg-reconfigure xserver-xorg

there you can give the detail vertical syncs and frecuency of your monitor

---

### Post by prshah on 2008-03-06
As suggested, use "sudo dpg-reconfigure xserver-xorg" command.

Or you can try Ctrl+Alt+"+" or Ctrl+Alt+"-" ("+"/"-" from the numeric keypad) to change resolutions on the fly (provided you have setup multiple resolutions in the first place!)

Cheers,
PRShah

---

### Post by denbeiren on 2008-03-06
> **scrooge_74 said:**
> did you try sudo dpkg-reconfigure xserver-xorg

there you can give the detail vertical syncs and frecuency of your monitor

Did the job,.. THX a million!

---

