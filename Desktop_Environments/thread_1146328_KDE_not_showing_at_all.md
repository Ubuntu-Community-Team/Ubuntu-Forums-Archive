---
title: "KDE not showing at all"
date: 2009-05-02
forum: Desktop Environments
---

### Post by richard_nl on 2009-05-02
Hi,

I just installed some updates and after I rebooted my pc my KDE desktop environment won't show up at all,not even a login :confused:. All I get is some red and pink distorted pixels on my screen. Does anyone have any suggestions what to do so I can use my DE again? I tried to remove my /home/username/.kde folder but that didn't do anything.

---

### Post by richard_nl on 2009-05-02
Alright so far it seems to be some kind of screen resolution problem. The splash screen is smaller when starting up. I tried to run xorg with the following
```

dpkg-reconfigure xserver-xorg

```
Half way setting the configurations I recieve a warning saying I have a custom setting and then it exits back to the terminal screen. Anyone got an idea how I can change the resolution or fix this xorg thing?

---

### Post by richard_nl on 2009-05-03
Problem solved it had to do with the lack of support for ATI cards.
solution found on the folowing thread.
[http://ubuntuforums.org/showthread.php?t=1133844&page=2](http://ubuntuforums.org/showthread.php?t=1133844&page=2)

---

