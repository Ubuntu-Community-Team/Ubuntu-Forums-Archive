---
title: "Cant disable tap to click"
date: 2010-02-03
forum: Desktop Environments
---

### Post by Mogath on 2010-02-03
Hey all,

Trying to disable tap to click on my 9.10 install on an MSI wind. Ive tried using the gconf-editor and can see that the value has changed (unchecked) but the touch to click is still enabled. I have rebooted with no change.

I do not see any options in the mouse settings either.

Seems rather simple. I must be missing something.

Thanks!

---

### Post by jeannacav on 2010-02-03
> **Mogath said:**
> Hey all,

Trying to disable tap to click on my 9.10 install on an MSI wind. Ive tried using the gconf-editor and can see that the value has changed (unchecked) but the touch to click is still enabled. I have rebooted with no change.

I do not see any options in the mouse settings either.

Seems rather simple. I must be missing something.

Thanks!

I am using 9.04, so it might be different, but you go to the mouse settings and there is a tab for touchpad. That is where I was able to disable mine.

jeanna

---

### Post by Mogath on 2010-02-03
Thanks Jeanna but unfortunately there is no panel for touchpad.

---

### Post by jeannacav on 2010-02-03
> **Mogath said:**
> Thanks Jeanna but unfortunately there is no panel for touchpad.

not panel
It is mouse panel and inside that there is a tab for touchpad??
sys pref>mouse> [general,or, accessibility,or touchpad]

ooo I am glad I waited,

jeanna

---

### Post by Mogath on 2010-02-03
I have general and accessibility but nothing else.

---

### Post by Mogath on 2010-02-04
Hmm...After loooking for hours last night I cant find a solution. I even tried Gsynaptics with no luck.

Why is this so difficult? Surely there are millions of laptops with ubuntu installed , and some subset of these could use an easy way to turn this off.

---

### Post by SushiR on 2010-02-04
Install gpointing-device-settings

---

### Post by Mogath on 2010-02-04
Just tried gpointing. It installed but only finds an explorer mouse, I dont have a mouse hooked up so I assume it thinks the trackpad is a mouse?

This is truly frustrating for something so simple.

Any other suggestions would be greatly appreciated.

---

### Post by Mogath on 2010-02-04
So I installed on a different laptop and Ubuntu was able to detect the trackpad and give me a panel to disable tap to click.

Is it safe to assume that the drivers for this touchpad are not available or arent working? Would that explain why I no matter what I do I cant disable it?

What I dont understamd is why using gconf-editor there is an option in the Ububuntu registry (? windows??) to turn it off but it doesnt do anything? Seems pointless? 

Should I just switch back to Windows on this computer? Why is this so difficult?

---

### Post by Cedders on 2011-03-05
tpconfig is probably also not worth trying.

[B]synclient MaxTapTime=0
[/B]
does seem to work for me for the current session.  See also [http://ubuntuforums.org/showthread.php?t=1457053](http://ubuntuforums.org/showthread.php?t=1457053)

---

