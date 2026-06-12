---
title: "multi monitor failure on wakeup (nvidia driver)"
date: 2015-06-03
forum: Desktop Environments
---

### Post by odror on 2015-06-03
I have had this problem for years. Now that I have connected to the same card (gtx 970) four monitors thing are worse.
I have 2 4k monitors 1 qhd and 1 FHD. Each time the monitors wake up from sleep they re-arranged. Sometimes 1 or two stay powered off.
sometimes the panning of a monitor is larger than the monitor size and is overlapping with the adjacent display.


I have the latest nvidia driver. 352.09

I think that because the monitors wake up at slightly different times. The driver gets confused and assumes that some are off and try to compensate for that.

I know that there is a bug in the driver. I am asking if any one knows of a workaround. A way to force the driver to stick with the configuration even if it "thinks" that the monitor is off.

May be there is a way to make the driver wait extra 2-3 seconds before it analyzes the connected monitors.

Thanks

---

### Post by tgalati4 on 2015-06-04
Is this a dual-boot machine?  Perhaps boot into Windows and see if your card can sleep and wake with 4 monitors correctly and consistently.

If you use the *nv* module, then you could make a manual configuration file (/etc/X11/xorg.conf) and hard-code the resolution and placement of all 4 displays.  However, you are then limited to the performance of the open driver, which you probably won't be happy with.

You would need a clever work-around.  Some displays will wake up when they detect a signal on an unused port, so if you have an extra HDMI port or VGA port, you could use that to wake up your display consistently.  

Send an email to the 352.09 developers and describe your experience.  Perhaps your input will improve the driver's reliability.

Go through each display's on-screen menu and set to "quick sleep" as opposed to "deep sleep".  Some displays have different levels of power saving and that affects wake-up time.

---

### Post by odror on 2015-06-04
> **tgalati4 said:**
> Is this a dual-boot machine?  Perhaps boot into Windows and see if your card can sleep and wake with 4 monitors correctly and consistently.

If you use the *nv* module, then you could make a manual configuration file (/etc/X11/xorg.conf) and hard-code the resolution and placement of all 4 displays.  However, you are then limited to the performance of the open driver, which you probably won't be happy with.

You would need a clever work-around.  Some displays will wake up when they detect a signal on an unused port, so if you have an extra HDMI port or VGA port, you could use that to wake up your display consistently.  

Send an email to the 352.09 developers and describe your experience.  Perhaps your input will improve the driver's reliability.

Go through each display's on-screen menu and set to "quick sleep" as opposed to "deep sleep".  Some displays have different levels of power saving and that affects wake-up time.

This is clearly linux driver issue  in windows it is not as bad. There is no panning of the display. All monitors are detected.
One of the problem is that all 4 monitors are of different manufactures. They wake up at  different times. (3 are on display port, one HDMI). I think that the nvidia driver tries to compensate for a "loss" of a monitor by re-arranging the monitor and sometimes by panning the display. All I want is that  the nvidia driver (and possibly gnome 3) will stick to the display setup and not try to "guess" what I want and change the monitors re-arrangement. This is clearly a bug in gnome/unity/nvdia. It has been there for many years. Things are now worse because I have 2 4k monitors (wake up slowly). I am looking for a workaround to force the display to my setup regardless of what the driver/display manager "think" is the correct setup because one monitor wake up too slowly.

This create a vicious cycle. Because a monitor wakes-up slowly. That display is being disabled by the diver. I have to go to the nvidia-seetings to enable it.

---

### Post by blm-ubunet on 2015-06-06
You can use xorg.conf with latest nvidia driver but that only reloads if X server restarts.
nvidia-settings will output your setup into xorg.conf (GUI & cmdline option).

nvidia-settings is a nv-control client & can be used from cmd line to do anything that the GUI allows.
You could try using nvidia-settings from the cmd line to reload the config file .nvidia-config-rc.
man nvidia-settings
```
nvidia-settings --load-config-only
```
Link this (in a script) to hotkey or udev rule.
You can load any config file, so could make good copy (working setup) to prevent overwrite.

---

