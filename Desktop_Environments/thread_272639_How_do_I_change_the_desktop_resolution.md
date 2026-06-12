---
title: "How do I change the desktop resolution?"
date: 2006-10-06
forum: Desktop Environments
---

### Post by Eyeore on 2006-10-06
I have a Compaq p1210 monitor and I'm trying to change the resolution to take advantage of the extra space. Currently it is stuck at 640x480. When I go to the screen resolution preferences, that is the only resolution in the list. I've tried running sudo dpkg-reconfigure -phigh xserver-xorg
 and it allows me to select the resolution I want, but when I return to the screen resolution preferneces, 640x480 is still the only one listed. I've also tried manually editing the xorg.conf file with sudo gedit /etc/X11/xorg.conf with no success. Is there something I'm missing?

---

### Post by wererabbit on 2006-10-06
When you edited your xorg.conf, did you put the resolution in on every line where it had repeating resolutions?  i.e.
"1024 x 768"  "800 x 600" etc.  (I think my syntax may be wrong there, I'm not at my box right now.)

I ran into the same issue and added the desired resolution to every line with resolutions in it, and it worked after that...
-w-

here's another thread that might help too:
[http://ubuntuforums.org/showthread.php?t=271010](http://ubuntuforums.org/showthread.php?t=271010)

---

### Post by Omnios on 2006-10-06
Another option is to press ctrl-alt  F-1 run 

```
sudo dpkg-reconfigure xserver-xorg
```

This will a turle like xorg config  program,  when you get to the video settings you will have a choice where you can I think its space to tick reselutions that you want to have.

---

### Post by CatKiller on 2006-10-06
You might have to manually put the refresh rates your monitor supports into your /etc/X11/xorg.conf. Either your monitor manual or the manufacturer's website will give you the information you need, and this forum will tell you how to do it.

---

### Post by strabes on 2006-10-07
video card drivers?

---

### Post by treborblack on 2006-10-08
i had the same problem yesterday and i've had 6.06 installed since its release. i rebooted half a dozen times to no avail and it a good job i had my son with me otherwise i'd have started tinkering.

left the pc unplugged for 24 hours and everything is back to normal. but is it:confused: i suspect a hardware failure is looming:evil:

---

