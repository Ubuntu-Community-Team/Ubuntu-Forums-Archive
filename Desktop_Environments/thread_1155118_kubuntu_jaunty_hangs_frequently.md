---
title: "kubuntu jaunty hangs frequently"
date: 2009-05-10
forum: Desktop Environments
---

### Post by aksheyjawa on 2009-05-10
Hello,

I have a HP dv2500 laptop. Earlier I had kubuntu 8.10 on it and it used to work fine. Recently I installed(fresh install, not an upgrade) Kubuntu 9.04 and since then it hangs frequently(few minutes to few hours after booting). I use-
[B]
CPU- Intel Core 2 Duo T2750 @ 2Ghz 
Display- Mobile GM965/GL960 Integrated Graphics Controller[/B]

**Usually the system hangs/freezes when I click on something. I can still move the mouse but the clicks are totally unresponsive. When I press the power off button on the laptop, it does not respond sometimes and at other times it does shutdown after going to a screen with lot of dotted lines(it does not show console messages of shutting down). **

Initially I thought it to be a hardware problem and so got my laptop serviced(and cleaned) to bring the CPU temperature down. Now temperature is fine but the system still hangs. **Recently I installed same kubuntu(9.04) on another system and that system also started giving same problem of hanging frequently.** Then I installed kubuntu 8.10 in that machine and it is running fine. So I infer that it should not be a problem with hardware. Please note that I had written my kubuntu 9.04 CD using the iso which I downloaded from internet. I had also checked its MD5 checksum after downloading. 

How can I figure out why the laptop is hanging? I checked the system logs but could not find any clue. Any help would be appreciated.

Thanks,
Akshey

---

### Post by glotz on 2009-05-10
Perhaps try another kernel.

---

### Post by pauljoseph on 2009-05-15
I also happen to have the same problem. My mouse can move, but no response from the desktop. The hangs appear randomly. Is there any update for this?

---

### Post by aksheyjawa on 2009-05-15
Putting the following lines in xorg.conf worked for me-


```
Section "Device"
        Identifier    "Configured Video Device"

        # ...
        Option        "AccelMethod" "uxa"
EndSection

```

Source:
1) [https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)
2) [http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/03/how-to-enable-uxa-at-ubuntu-jaunty.html)


If the above thing does not work for you then you can try this option-
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by pauljoseph on 2009-05-16
Thanks,
it helps so far, I haven't had any crash after adding uxa. I will post again if I experience any problem.

---

