---
title: "gnome classic in 12.04: too narrow window resizers and wrong position of buttons"
date: 2012-07-20
forum: Desktop Environments
---

### Post by dl4oce on 2012-07-20
Hi,

I was pretty happy that u 12.04 runs much much faster on my "SSD powered" hardware than the LTS version before AND supports a fallback to gnome 2 which I do prefer a lot to unity.

But at least two things are getting annoying:

1. Why is the area which is used to point at to resize windows only 2x2 pixels large? Or even 1x1 pixel? Can't tell. But it's hard work to find it. How can it be made broader? I also don't need narrow scroll bars that are hard to hit.

2. Haven't found a way to place the buttons minimize, maximize, close in the upper right corner of a windows - any news on this?


Arne

---

### Post by ajgreeny on 2012-07-20
The resize problem is more related to theme, I believe, but there are not as many themes available in the default install of 12.04 as in previous ubuntu versions.  Have a good look at [GNOME-Look.org]("http://gnome-look.org/")  for gtk3 themes and see if you can find anything that looks more appropriate.

The close/minimise/maximise button placement is still possible using information from [http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) which I recommend you look at carefuuly as it will give you lots more configuration options for the fallback DE of12.04.  However, as a quick answer run ```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,spacer,close"
``` in terminal and you'll get what you want with the addition of an extra space between the close button and the min/maximise buttons, which I like.

If you find a theme that works well for you, let us know, as the resize problem is quite widespread.

---

