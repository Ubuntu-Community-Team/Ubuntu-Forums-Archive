---
title: "Syste hangs during &quot;quiet splash&quot;"
date: 2009-05-24
forum: Desktop Environments
---

### Post by SDSL on 2009-05-24
Hello, I've upgraded to Ubuntu karmic 9.10
but now i cant boot using the "quiet splash" mode
i had to boot using the "single"(recovery mode) then choose NORMAL from the recovery menu


note:-
kernel version : kernel 2.6.30-5
device: Acer Aspire 3102WLMi/AMD/ATI X1100
everything (sound/lan/wlan/graphics) works fine from withing the recovery mode

any help is much appreciated

---

### Post by glotz on 2009-05-24
Edit the kernel line in grub and remove quiet and splash to see what goes south.

---

### Post by SDSL on 2009-05-24
well, it works!
after removing "quiet splash" options from grub.

what that mean? i have something messing?
Thanks

---

### Post by whoop on 2009-05-24
Maybe your graphics card or monitor can't handle the resolution or settings of the splash screen. I had this years ago with an nvidia card when I changed monitors. I had to add some custom vga setting to the kernel line in menu.lst
Here it is:
[http://ubuntuforums.org/showthread.php?t=507881](http://ubuntuforums.org/showthread.php?t=507881)

---

### Post by SDSL on 2009-05-24
Thanks, adding the option vga=0x318 works
and now i can see the splash screen
perfect!

---

### Post by whoop on 2009-05-24
> **SDSL said:**
> Thanks, adding the option vga=0x318 works
and now i can see the splash screen
perfect!

Glad that worked, however if I understand you correctly you where not able too boot into X at all without the vga modification in the kernel line. I think this is quite serious and needs to be fixed. Not everybody knows or wants to be editing config files. It especially bugs me because I had this years ago.

Could you provide us with details about your graphics card and monitor? You should post a bugreport. If you do not feel like doing that I would be happy to post that for you.

---

### Post by SDSL on 2009-05-24
The Graphic card is ATI Radeon Xpress 1100
it was not recognized but was working, then i installed "envyng-core" package which fixed the vga adapter driver, but even after fixed i was not able to log using the "quiet splash" mode
Monitor: um..as stated into post #1 it's laptop Acer

I was actually able to log into X using the (recovery mode)  " 'single' kernel option"

when i was login using the "quiet splash" the default option, it was loading then just Hangs before the login screen appears. and i wasn't able to see the "loading progress" ( the splash screen ).

in case it's a bug, i would like to know how to submit logs(terminal commands) for it
i might go back and edit grub to "quiet splash" and make any logs wanted for the bug report

I'll be happy to file the bug report

ps: I've one more bug. "mouse clicks with touchpad is disabled" even when i enable it from "system-> pref -> mouse", just using the buttons to click but not through the touchpad..it was working well on "jaunty"

---

### Post by whoop on 2009-05-24
> **SDSL said:**
> The Graphic card is ATI Radeon Xpress 1100
it was not recognized but was working, then i installed "envyng-core" package which fixed the vga adapter driver, but even after fixed i was not able to log using the "quiet splash" mode
Monitor: um..as stated into post #1 it's laptop Acer

I was actually able to log into X using the (recovery mode)  " 'single' kernel option"

when i was login using the "quiet splash" the default option, it was loading then just Hangs before the login screen appears. and i wasn't able to see the "loading progress" ( the splash screen ).

in case it's a bug, i would like to know how to submit logs(terminal commands) for it
i might go back and edit grub to "quiet splash" and make any logs wanted for the bug report

I'll be happy to file the bug report

ps: I've one more bug. "mouse clicks with touchpad is disabled" even when i enable it from "system-> pref -> mouse", just using the buttons to click but not through the touchpad..it was working well on "jaunty"

You can post bugs on launchpad.net. Just create an account there see if your bug is already posted; if it is (possibly) add comments to that or else create your own bugreport.

---

