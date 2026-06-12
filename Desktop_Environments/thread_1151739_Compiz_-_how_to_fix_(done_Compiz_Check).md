---
title: "Compiz - how to fix (done Compiz Check)"
date: 2009-05-07
forum: Desktop Environments
---

### Post by den160593 on 2009-05-07
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

### Post by joewski on 2009-05-07
> **den160593 said:**
> Hi. I'm using a Dual-Screen layout on my Ubuntu. I was wondering if it was possibly to get Compiz to run. Here is the output on Compiz Check.

So if I switch back to 1 screen, enable Compiz, and then enable 2 screens again will it work? I'm just cautious because last time I played around with Compiz I caused my graphics drive to corrupt which took me a fair amount of time to fix.

Thanks
-Den

I found Compiz is tricky at times, I've been playing with it alot on a few machines so Im getting some feel for it.

I found that compiz doesn't work if your the second user. Also it sometimes doesn't work if you have manually played with the xorg configuration files. 

Heres my suggestions on getting it working.

First try getting it to work with only one screen.
That way you know that the drivers are capable of doing the job.
You will need to reboot the machine to ensure that the hardware is rescanned.

Also after playing I have killed my compiz on my laptop with a 2nd monitor.
What I did to fix it is run this command.

$ sudo dpkg-reconfigure xserver-xorg

This command resets the xserver configuration file. I could then get compiz to activate.

---

