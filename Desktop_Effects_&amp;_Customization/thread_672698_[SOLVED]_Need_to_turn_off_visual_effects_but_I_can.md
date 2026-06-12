---
title: "[SOLVED] Need to turn off visual effects but I can't"
date: 2008-01-19
forum: Desktop Effects &amp; Customization
---

### Post by MountainX on 2008-01-19
I enabled extra visual effects and now I have no content in any windows. Therefore I cannot open the appearance tool to turn off visual effects. I have started X in failsafe mode and attempted to turn off visual effects, but they are already off in that mode. Every time X starts normally, I get a desktop in which I can't do anything. How can I disable visual effects from failsafe mode? Thanks

(Why is it so hard to get Compiz Fusion working with dual monitors?)

---

### Post by FuturePilot on 2008-01-19
Press Alt+F2 and enter
```
metacity --replace
```

---

### Post by MountainX on 2008-01-19
I could not type into any windows, including that one. So what I did was start X in a failsafe GNOME session and rename /usr/bin/compiz to compiz.disabled. Then when X started normally I was back to a working desktop with no visual effects.

It's amazing that I can't get visual effects to work. I've been on it all day.

And it sucks that I lost my sound after using Envy to get the latest nVidia drivers. Does anyone have sound on Gutsy 64bit with latest nVidia drivers via Envy?

I might just install from scratch and forget about Compiz because I don't think it's going to work. And if I don't use visual effects, I don't need Envy to get the latest nVidia drivers, so that should give me my sound back.

I sure would have liked to have this, but I guess it isn't going to happen with my computer:
[http://youtube.com/watch?v=y7CGLEZXDSM](http://youtube.com/watch?v=y7CGLEZXDSM)

---

### Post by fracturedmorals on 2008-01-20
Type "Ctrl + Alt + F1"

Login to the terminal. Type "pkill compiz"

Type "Alt + F7"

If you have no borders around your windows, tpye "Alt + F2" and enter "metacity"

---

### Post by MountainX on 2008-01-20
> **fracturedmorals said:**
> Type "Ctrl + Alt + F1"

Login to the terminal. Type "pkill compiz"

Type "Alt + F7"

If you have no borders around your windows, tpye "Alt + F2" and enter "metacity"

Thanks. That helps. But I still have a problem. When I came back into the GUI my visual effects were set to none. But then when I restarted X, the extra visual effects were automatically enabled again and the GUI becomes unusable (can't give input into any window). 

What config file should I edit to make sure X starts with no visual effects? Thanks.

---

### Post by Ub1476 on 2008-01-20
It's very strange you lost your sound when using Envy. I guess it has something to do with the x86_64 system, so I would go for 32-bit. It's really not much difference, unless you plan on ripping lots of lots of Cds. Anyway, I recommend you to do a clean install (only one monitor plugged), install Envy (if you dare), plug in the monitor and select it in the System>Admin>Screen and Graphics.

---

### Post by MountainX on 2008-01-20
Thanks. I guess it is time for a clean install. I'm new to Linux, so this will be a good learning experience for me.

---

### Post by Ub1476 on 2008-01-20
> **MountainX said:**
> Thanks. I guess it is time for a clean install. I'm new to Linux, so this will be a good learning experience for me.

Yes, I remember when I was new to Linux (Ubuntu 6.10) I had to do a couple of installs, due to my ATI driver. It's a shame that there is no "system restore" utility for Linux..

---

