---
title: "Intel i810 Graphics Screen Resolution"
date: 2009-04-29
forum: General Help
---

### Post by icanfly0307 on 2009-04-29
Hi,
   In Ubuntu 8.10, I couldn't get my graphics card (Intel 82815) to run at 1024x768 on my laptop. A lot of people had also run into this issue and were complaining that they couldn't get anything above 800x600. I was just wondering if this problem has been fixed in 9.04? I'm going to install Ubuntu in a few hours and I just wanted to get a heads up on what the graphics card situation is currently like. Thx for your help...

---

### Post by Thelasko on 2009-04-29
While I don't know if it's been fixed, I know how to fix it if it's still broken.

First, use the "intel" driver not the "i810."

Second, add the following lines to xorg.conf in the "screen" section.

```
       SubSection "Display"
           Depth		24
           Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
           # ADD A VIRTUAL LINE TO PROVIDE FOR THE LARGEST SCREENS YOU WILL HOTPLUG 
           Virtual              2048 2048 
       EndSubSection
```

Logout and login and you're done.

In my opinion, Hardy has the best Intel drivers.  After Hardy, the developers have been trying to increase performance, which has taken it's toll on reliability.

---

### Post by icanfly0307 on 2009-04-30
yeah, the problem's been fixed. i used my xorg.conf from fedora and it's working fine. i had to replace "i810" with "intel" though. thx for your help...

---

### Post by Thelasko on 2009-04-30
> **icanfly0307 said:**
> yeah, the problem's been fixed. i used my xorg.conf from fedora and it's working fine. i had to replace "i810" with "intel" though. thx for your help...

Xorg.conf should be mostly blank in Ubuntu.  The newer versions of Xorg automatically detect all of your hardware.

But if it works, it works!

---

### Post by whayong on 2009-04-30
Not working out of the box for me.  I'm stuck @ 800X600.  How does one change/make sure that they are running the "Intel" driver as opposed to the "i810" driver in Jaunty?

---

### Post by Thelasko on 2009-05-01
> **whayong said:**
> Not working out of the box for me.  I'm stuck @ 800X600.  How does one change/make sure that they are running the "Intel" driver as opposed to the "i810" driver in Jaunty?

It appears the "i810" drivers have been discontinued in Jaunty, so you should be running "Intel".

Try editing xorg.conf the way I posted above.  The i810 cards don't like to detect monitor settings for some reason.  Making those changes overrides monitor detection.

---

