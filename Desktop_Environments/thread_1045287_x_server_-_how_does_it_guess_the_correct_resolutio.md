---
title: "x server - how does it guess the correct resolution?"
date: 2009-01-20
forum: Desktop Environments
---

### Post by bazzer on 2009-01-20
So how does it guess then? Does it query the graphics card for a 'max' mode, then then monitor (edid?) and use the highest one available?

I'm having an issue. I need to be able to reliably set the screen resolution, regardless of hardware, via a command line. So, either in /etc/xprofile or /etc/gdm/PreSession/Default.
I've been using xrandr -s 1280x1024 up until now, but in Intrepid, the 'detected' modes don't include the one I want - on all hardware.

A further annoyance is that the gdm greeter is outside of this xrandr control.

I think the answer is going to be a 'create your own xorg.conf' and see how you get on. So how can I do that (how did 7.10 and before do it?) and moreover, why should I have to? Why won't it 'just work'? Windows does.

---

### Post by oaqster on 2009-01-20
yup, xorg probes and detects your monitor and its modes at startup and selects the highest one available.  if for some reason your edid is not probable it will go to a bad res, some vga drivers will let you provide edid info for your display through a file as opposed to probing it. i had to go that route as edid probe was failing for me due to my KVM.

[http://ubuntuforums.org/showthread.php?t=1038933](http://ubuntuforums.org/showthread.php?t=1038933)

for a different res instead of the max, you can add modelines to your xorg.conf file, which is an ordered list of modes that X should try using first, however i believe if they dont match up with your display's edid xorg might just remove them.

hope this helps
- oaqster

---

### Post by bazzer on 2009-01-23
Well I seem to have at least got everything working when the user logs in...

In /etc/xprofile:
```
xrandr --newmode "1280x1024_60" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
xrandr --addmode VGA 1280x1024_60
xrandr --output VGA --mode 1280x1024_60
```

But GDM is still the wrong resolution, despite the background image being the correct size. :(

---

