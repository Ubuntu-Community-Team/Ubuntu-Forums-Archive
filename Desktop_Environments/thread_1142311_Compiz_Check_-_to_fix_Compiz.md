---
title: "Compiz Check - to fix Compiz"
date: 2009-04-29
forum: Desktop Environments
---

### Post by den160593 on 2009-04-29
Hi. I'm using a Dual-Screen layout on my Ubuntu. I was wondering if it was possibly to get Compiz to run. Here is the output on Compiz Check.

> denis@denis-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV350 AR [Radeon 9600]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ [COLOR="Lime"]OK[/COLOR] ]
 Checking for non power of two support...          [ [COLOR="Lime"]OK[/COLOR] ]
 Checking for composite extension...               [ [COLOR="Lime"]OK[/COLOR] ]
 Checking for FBConfig...                          [ [COLOR="Lime"]OK[/COLOR] ]
 Checking for hardware/setup problems...           [[COLOR="Red"]FAIL[/COLOR]]

There has been (at least) one error detected with your setup:
 **Error: Your current resolution is too high to run Compiz. **

Would you like to know more? (Y/n) y

 Your resolution is **2560x1024** but the maximum 3D texture size that your
 graphics card is capable of is **2048x2048**. Thus Compiz will not be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again). 



So if I switch back to 1 screen, enable Compiz, and then enable 2 screens again will it work? I'm just cautious because last time I played around with Compiz I caused my graphics drive to corrupt which took me a fair amount of time to fix.

Thanks
-Den

---

