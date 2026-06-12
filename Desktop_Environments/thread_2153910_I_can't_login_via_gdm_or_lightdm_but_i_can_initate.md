---
title: "I can't login via gdm or lightdm but i can initate xorg using startx"
date: 2013-06-12
forum: Desktop Environments
---

### Post by jfca283 on 2013-06-12
Hello
My problem is now, after an upgrade from 12.10 to 13.04, i can't login via gdm or lightdm. The screen offers me "run in low graphics mode" but it doesn't responde to any action. However if i do ctrl alt f1, login and then startx on console, i can see my desktop and working normally. How do i fix that? My video card is ATI HD6300. Thanks for your time and interest.

---

### Post by 2Stoned on 2013-06-14
You may need to re-install the DM? But you can try to reconfigure lightdm after you initiated startx from the console. Open the terminal: ```
sudo dpkg-reconfigure gdm
``` and select lightdm. After that ```
sudo dpkg --configure -a
```
Restart ubuntu.

Or if you use a laptop, try using  the FN+F8 button to adjust brightness. Sounds silly but this seem to  work for some. Hope this helps?

---

### Post by jfca283 on 2013-06-15
I messed up all now. For some reason i installed the ati oficial driver. Now when i do ctrl alt f1, my screen goes to black and i can't do anything. I lost the ability to run startx from console to call xorg. Should i install flglx again? How? Damn, i'm writing from windows and i hate it. Help me please.

---

### Post by 2Stoned on 2013-06-15
I think there are some problems with the ATI drivers and fglrx packages when installed together. Try to remove the fglrx drivers from the system: ```
sudo apt-get remove fglrx*
``` or for complete removal ```
sudo apt-get --purge remove fglrx*
```

Restart ubuntu.. Or do this for the ATI drivers and re-install the fglrx drivers.


Check out:
[https://bugs.launchpad.net/fglrx/+bug/1068661/+index?comments=all](https://bugs.launchpad.net/fglrx/+bug/1068661/+index?comments=all)
[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work)

---

### Post by jfca283 on 2013-06-15
And i must do it from recovery mode? failback?

---

### Post by 2Stoned on 2013-06-16
What do you see when the system boots? Try to enter recovery mode and then uses the no mode set.. i don't know if this will work. What did you tried so far?

---

