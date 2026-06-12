---
title: "Using unity seems to be laggy and generaly slow"
date: 2011-10-14
forum: Desktop Environments
---

### Post by wardy277 on 2011-10-14
i have recently upgraded from 11.04 to 11.10. I was usign gnome2 clasic before and was quite looking forward to trying the new and improved unity in 11.10.

After a while of using Unity i have found it a bit clunky and slow. I am a web developer so i spend most of my time going between firefox and aptata, both of which seems to be very slow and laggy when scrolling up and down. Simply scrolling up and down a page looking through code is very laggy.

Has anyone else had this issue? also, unity in general seems slow, especially the alt-tab switcher

When i switch from unity to gnome classic (with effects) all of my problems away, firefox and apatana are very quick and the system i general feels quicker

I am running on an Intel Core2Quad Q82000, 6Gb RAM, Ubuntu X64, Nvidia GeForce 310 (512Mb) v280.13

---

### Post by collisionystm on 2011-10-14
> **wardy277 said:**
> i have recently upgraded from 11.04 to 11.10. I was usign gnome2 clasic before and was quite looking forward to trying the new and improved unity in 11.10.

After a while of using Unity i have found it a bit clunky and slow. I am a web developer so i spend most of my time going between firefox and aptata, both of which seems to be very slow and laggy when scrolling up and down. Simply scrolling up and down a page looking through code is very laggy.

Has anyone else had this issue? also, unity in general seems slow, especially the alt-tab switcher

When i switch from unity to gnome classic (with effects) all of my problems away, firefox and apatana are very quick and the system i general feels quicker

I am running on an Intel Core2Quad Q82000, 6Gb RAM, Ubuntu X64, Nvidia GeForce 310 (512Mb) v280.13

Try gnome-shell. It may be faster for you.

---

### Post by coffeecat on 2011-10-14
> **wardy277 said:**
> 
Has anyone else had this issue? also, unity in general seems slow, especially the alt-tab switcher


Using a not-state-of-the-art ATI card (Radeon HD5450) and the open source driver, Unity in 11.10 is zippy enough for me and the alt-tab switcher is fine. That's with dual-monitors too. Yours sounds like a video driver issue. I'm not really up on the latest nvidia cards and yours sounds to be fairly recent one. Which video driver are you using?

---

### Post by wardy277 on 2011-10-14
i am running the nvidia official driver 280.13 do you think this could simply be a graphics issue?

could be issue be related to my upgrading from using gnome2?

---

### Post by coffeecat on 2011-10-14
> **wardy277 said:**
> i am running the nvidia official driver 280.13 do you think this could simply be a graphics issue?

To be honest, I don't know. All I can say is that I have both Natty and Oneiric on adjacent partitions on this machine and Unity works just fine in both for me. And I have no experience of nvidia cards beyond the now somewhat middle-aged GeForce 8400GS.

When you say "classic desktop", is that the gnome-panel gnome2 near-lookalike but based on gnome3 that you get with the gnome-session-fallback package?

---

### Post by wardy277 on 2011-10-14
> **coffeecat said:**
> 

When you say "classic desktop", is that the gnome-panel gnome2 near-lookalike but based on gnome3 that you get with the gnome-session-fallback package?

Yes that what i am using at the moment with compiz effects turned on. that is what led me to believe it was unity

---

### Post by coffeecat on 2011-10-14
> **wardy277 said:**
> Yes that what i am using at the moment with compiz effects turned on. that is what led me to believe it was unity

Interesting. Unity is a bit heavier on resources than other compiz effects, so perhaps it's a marginal thing with your particular GPU/driver combination. One thing you could try. In compizconfig-settings-manager > Desktop > Unity Plugin > Experimental tab, try changing Dash blur to anything but active blur. Active blur is a bit demanding.

---

### Post by rodmachado on 2011-10-14
I had the same problem, and it was mainly because of problems of compiz and nvidia-current (the proprietary driver) not talking to each other properly.

Try to uninstall nvidia-current  (or any other version of the proprietary driver) and reboot:

```

sudo apt-get remove nvidia-current

```Then, on the next system initialization, the opensource nouveau driver will load, and for me it works well with unity. I believe (and this is only a guess) that this problem may be solved with the release of the upcoming 285 version of the binary drivers...

I hope this solves your issue

---

### Post by wardy277 on 2011-10-14
I have been playing with the settings and decided to go back to the unity ubuntu session.

at first it was quick and i didnt have any issues, then i played with a few settings and disabled unity from compiz settings manager, after re enabling it it all went laggy again. i logged out and back in again and it all seems fine again. maybe there are some unity bugs to be ironed out. 

i did notice that aptana was usign the new scrollbars, but when i scrolled down there was a flickering orange bar above or below (depending on if i was scrolling up or down). I have disabled the scrollbars for aptana by adding this to the launcher script: export LIBOVERLAY_SCROLLBAR=0

---

### Post by mc4man on 2011-10-14
> **wardy277 said:**
> .
. Simply scrolling up and down a page looking through code is very laggy.

Has anyone else had this issue? 


i have definitely noticed thru much of the dev of 11.10 a bit of a lag in scrolling in FF & to a lesser extent in google-chrome
Though here it was generally confined to the initial scroll of a page - after which it would be normal

What was also seen here with compiz-0.9+, (on a laptop), was a small lag  in the upclocking from performance level 0 to the higher levels 1, 2
The most obvious way to see that here was to open an unmaxed window, wait about 30 sec for the adaptive clocking to drop to 0 & then pick up & move the windows. A fairly noticeable lag in response is seen.

This is not seen in unity-2d, GS or unity in 11.04 on this hardware

I will say that now I'm trying the latest compiz from proposed & then effect is lightened but still there.
( if I temp change from adaptive to max performance then this doesn't happen & FF scrolling is also good

---

### Post by mc4man on 2011-10-16
Personally (with this laptop & nvidia), I think there has been a regression in 11.10/unity/compiz
Have re-opened my bug on, for all I know it's just me

for the moment I've made an adjustment in xorg.conf - this sets the card to full performance on AC, adaptive on battery
FF works fine now as does compiz actions.
Whether I kept this depends on whether there is any temp issues - this laptop has crappy cooling so I'll have to see

Bug report
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/843383](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/843383)

new  xorg
```
Section "Device"
  Identifier "NVIDIA GeForce"
  Driver     "nvidia"
  Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
EndSection

```

---

