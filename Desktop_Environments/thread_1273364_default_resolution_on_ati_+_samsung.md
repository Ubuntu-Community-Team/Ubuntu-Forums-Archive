---
title: "default resolution on ati + samsung"
date: 2009-09-23
forum: Desktop Environments
---

### Post by kenshir on 2009-09-23
I found in an old topic, that is now read-only, a useful suggestion that solved a resolution problem I had, so I'm opening this new thread as a reference.
This is the original one:
[http://ubuntuforums.org/showthread.php?t=359310](http://ubuntuforums.org/showthread.php?t=359310)

My default login screen resolution on Ubuntu 9.04, Ati 4850, Samsung T220HD monitor , was 1920x1080, too much.

Thanks to stinkball's suggestion, I used this command

sudo aticonfig --resolution=0,1680x1050,1920x1080,1280x1024,1280x768,1024x768,800x600,640x400

and it worked like a charm: now login screen is set at 1680x1050 instead of 1920x1080.

Nevertheless, this solved my main problem: before this tweak, every time I switched my monitor between television source and hdmi source, I had a wrong resolution 1920x1080.
Now the monitor is keeping the right resolution, 1680x1050.

Hope this can help someone.

---

### Post by clonne4crw on 2009-09-27
So just using the ATI tool or the Gnome screen resolution configuration tool to change your resolution when switching monitors doesn't work anymore?

---

