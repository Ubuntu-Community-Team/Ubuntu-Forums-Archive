---
title: "Desktop Effects Cannot Be Enabled"
date: 2007-12-16
forum: Desktop Effects &amp; Customization
---

### Post by xItachi on 2007-12-16
Hi, before when I enabled Extra Visual Effects, it has always worked, but today it stopped working and gives me a message saying "Desktop Effects could not be enabled." I think it was because I tried plugging my sister's monitor to my laptop.  I wanted to try and have my  workspace 1 on my laptop and workspace 2 on her monitor, but when I plugged it in, the monitor wasn't detected.  I go to the Screens and Graphics preferences and for Screen 1, it says Plug and Play Monitor (it has always said that, even before when it worked) and for Screen 2, it just said 'Disabled', and the radio buttons for primary monitor or secondary screen was greyed out / disabled.  So I just took out the monitor cable and rebooted my computer.  After the reboot, it said Ubuntu was running in low graphics mode and visual effects would not be able to run unless I configure my graphics settings.  When I go to the Screens and Graphics preferences again, I see that the settings for Screen 1 and Screen 2 are the same except now for Screen 1, the resolution is set at 1024x768 & 61 Hz refresh rate, while before it was 1280x800 & 60 Hz.  Screen 2 is the same (disabled), but now the radio buttons for 'primary monitor' and 'secondary monitor' are not greyed out and I can select them.  If anyone knows what happened or can help, I would really appreciate it.  Thank You.

---

### Post by Ub1476 on 2007-12-16
Can't help you with how to set up two monitors, but I guess your xorg.conf were cluttered in the try.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by xItachi on 2007-12-16
That didn't seem to work.  I still could not enable Extra Visual Effects and my screen resolution still stays at 1024x768 with 61 Hz refresh rate.  Thanks for trying though.

---

