---
title: "Intel 965 Graphics Problems with Gutsy Gibbon"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by Doughy on 2007-10-19
I just installed Ubuntu 7.10 Gutsy.  I am currently running my graphics with the integrated chip on my Intel 965 motherboard.  I am having some issues, and wondering if anyone out there knows how I can fix them.

[LIST=1]
[*]Desktop effects will not enable.  Right now, when I look at the driver that is being used it just says it is the "vesa compliant driver."
[*]Is there a better driver that I should be using for the intel 965 chip?  I tried changing to different drivers in the new "screens/graphics" control panel, but nothing else worked.
[*]My monitor (ACER AL1916) does not support some of the refresh rates that some of the drivers are trying to put out.  How can I make the drivers use only refresh rates that my monitor supports?  I tried setting my monitor in the "screens/graphics" panel to my model, but only the "plug n' play" monitor setting seems to work.
[/LIST]

I thought X.org was supposed to be way better for intel graphics.  I also thought that intel open-sourced their 965 graphics driver, so why is it so spotty?  Any help or answers to any of these questions is appreciated.  Thanks.

---

### Post by asjadjawed on 2007-10-20
Also have a 965 and just got gutsy.

Found this:

[http://ubuntuforums.org/showthread.php?p=3560572](http://ubuntuforums.org/showthread.php?p=3560572)

Completely cured my system and now my machine can run compiz and yeah compiz is gorgeous.

---

### Post by asjadjawed on 2007-10-20
One thing more before you try my earlier post go to System>Administration>Screen and Graphics and select the correct model of your chipset/graphic card (in this case intel>965) and your monitor.

Enjoy!

---

### Post by Doughy on 2007-10-20
Thanks for your post.  I tried the change and it didn't work for me.  Oh well.

I am basically fed up with this intel 965 integrated graphics.  I am going to order a new graphics card today, probably nvidia.  Integrated graphics just aren't that good, especially this 965 driver.

---

### Post by sixstorm on 2007-10-20
> **Doughy said:**
> Thanks for your post.  I tried the change and it didn't work for me.  Oh well.

I am basically fed up with this intel 965 integrated graphics.  I am going to order a new graphics card today, probably nvidia.  Integrated graphics just aren't that good, especially this 965 driver.

The 965 chipset is great for CF!  I finally got it to work today by installing xserver-xorg.  Go to System->Preferences->Appearance and then Visual Effects.  Try to enable Extra and see what happens.  It's gorgeous!

---

