---
title: "powertop detects too many wakeups on XPS m1330"
date: 2008-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nightfrost on 2008-05-09
```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 3,1%)
C1                0,0ms ( 0,0%)
C2                0,5ms ( 0,8%)
C3                5,4ms (96,1%)


Wakeups-from-idle per second : 193,6    interval: 10,0s
no ACPI power usage estimate available

Top causes for wakeups:
  32,1% ( 74,0)       <interrupt> : i915@pci:0000:00:02.0 
  31,3% ( 72,1)      <kernel IPI> : Rescheduling interrupts 
   5,2% ( 12,0)       <interrupt> : iwl4965 
   5,0% ( 11,4)       compiz.real : schedule_timeout (process_timeout) 
   4,8% ( 11,0)       <interrupt> : libata 
   4,3% ( 10,0)     <kernel core> : ehci_work (ehci_watchdog) 
   3,5% (  8,0)      <kärnmodul> : usb_hcd_poll_rh_status (rh_timer_func)
   3,0% (  6,8)       <interrupt> : extra timer interrupt
   2,3% (  5,4)       <interrupt> : PS/2 keyboard/mouse/touchpad
   1,6% (  3,7)              Xorg : schedule_timeout (process_timeout)
   1,0% (  2,3)   thunderbird-bin : futex_wait (hrtimer_wakeup)
   0,9% (  2,0)   multiload-apple : schedule_timeout (process_timeout)
   0,7% (  1,6)    wpa_supplicant : schedule_timeout (process_timeout)
   0,5% (  1,1)       gnome-panel : schedule_timeout (process_timeout)
   0,5% (  1,1)           firefox : futex_wait (hrtimer_wakeup)

```

This is an idle session under GNOME. It can't be normal, can it? The i915 interrupts I guess is compiz. But how do I get rid of the rescheduling interrupts (they're always there), why is libata showing up so high? And what is ehci_work? This, alongside "extra timer interrupts" and "usb_hcd_poll_rh_status" are things I haven't seen on my other (older) laptop.

Any help appreciated!

---

### Post by nightfrost on 2008-05-09
I just tried booting from the Fedora9 live CD, which sports the 2.6.25 kernel. It was still showing quite a few rescheduling wakeups, but not nearly as much as ubuntu. I then installed a 2.6.25 kernel using the kernel teams ppa. After enabling sync to vblank in compiz _and_ using the new kernel it seems that not only did the i915 wakeups disappear, but the rescheduling got much less aggressive.

Any comments on this?

---

### Post by nightfrost on 2008-05-09
Oh, my god this is annoying.

Using the 2.6.25 kernel, or even the drm modules from git, decreases the wakeups considerably (although 2.6.25 seems to be better with or without compiz running). However, the drm modules that are shipped with 2.6.25 as well as the ones from git, fail to resume the screen. Heh. I'm getting so tired of all these little issues.

Still, if anyone has any suggestions, please let me know.

---

### Post by sdennie on 2008-05-10
It might be useful to see the output while on battery power to see what your idle wattage is like after about a minute.  I have the same laptop except with an nvidia card and, with the exception of the interrupts from the i915 (which are probably driving up the kernel IPI interrupts at the same time), those numbers seem reasonable.  

My m1330, with usual apps like pidgin, epiphany, nautilus and terminals running general has about 90 wakeups a second.  When I went out of my way to really try to reduce the wakeups, I got them down to around 15-20 but, the extra power savings was only about .3 watts while idle so, I think after a certain point, there are diminishing returns to reducing wakeups.

Note: libata is disk related and ehci_work is usb related.  Do you have an external usb drive plugged in?

---

### Post by nightfrost on 2008-05-10
Thanks a lot for the reply!

On battery the watt usage varies from 15 to 20 Watts. How does it look with your nvidia chip?

I think you're right about the i915 wakeups driving up the rescheduling. Newer drm modules fix that problem, but they break opengl after resume. I'm trying to find a fix for that.

What's strange about the high libata and ehci_work wakeups is precisely that as far as I know the hard drive's not spinning, and I had no USB device connected to the laptop. Maybe the ehci_work wakeups are caused by the internal webcam which uses the ehci_hcd module?

---

### Post by wipet on 2008-05-10
You should try the tips and tricks at this site: [http://www.lesswatts.org/](http://www.lesswatts.org/)
I made a script in /etc/acpi/battery.d that run every time I'm on battery with all those tips and I keep my consommation between 11 and 15 watts most of the time with a NVIDIA card (with the latest beta driver) on my m1330, with my brightness at 5/7, wifi on.

Reducing wakeups was far less useful for me to reduce my power consumption.

---

### Post by nightfrost on 2008-05-10
> **wipet said:**
> You should try the tips and tricks at this site: [http://www.lesswatts.org/](http://www.lesswatts.org/)
I made a script in /etc/acpi/battery.d that run every time I'm on battery with all those tips and I keep my consommation between 11 and 15 watts most of the time with a NVIDIA card (with the latest beta driver) on my m1330, with my brightness at 5/7, wifi on.

Reducing wakeups was far less useful for me to reduce my power consumption.

That is indeed a great site, and in fact where I have gathered tips and tricks before. But I seldom get down to 11-15 watts on my m1330. I'll try some more later. Have you applied any kernel patches or do you use the stock Hardy kernel?

---

### Post by wipet on 2008-05-10
> **nightfrost said:**
> That is indeed a great site, and in fact where I have gathered tips and tricks before. But I seldom get down to 11-15 watts on my m1330. I'll try some more later. Have you applied any kernel patches or do you use the stock Hardy kernel?

I'm using the stock Hardy kernel. Maybe my usage is less ressource intensive than yours. My typical usage is web browsing/note taking with Pidgin running, bluetooth off, and I almost never listen to music when on battery, I also avoid complex compiz animations that make my graphic card going into full power. I also got the LED screen and a 1.66ghz core 2 duo, wich is not that powerful...

---

### Post by nightfrost on 2008-05-10
> **wipet said:**
> I'm using the stock Hardy kernel. Maybe my usage is less ressource intensive than yours. My typical usage is web browsing/note taking with Pidgin running, bluetooth off, and I almost never listen to music when on battery, I also avoid complex compiz animations that make my graphic card going into full power. I also got the LED screen and a 1.66ghz core 2 duo, wich is not that powerful...

My usage is pretty much the same as yours. I have the 1.8GHz CPU which is pretty weak as well. The only difference is that I can't live without compiz so I have that running.

It's becoming more and more obvious that the problem here is with the i915 drm module. I think if I get that fixed I can get some nice power saving.

Anyway, thanks a lot for the input!

---

### Post by nightfrost on 2008-05-10
ok, got it now.
ehci_works wakes up due to the web cam (uvcvideo module)
and libata wakes up due to hal's polling of the CD drive.

I hope these get fixed sometime soon.

---

### Post by sdennie on 2008-05-10
My power consumption with a T9300 (2.5Ghz), nvidia, LED display at 4/7, wifi on, compiz on, and common apps running is between 12.5W and 13W while relatively idle.  That's down from about the 18ish that I got by default in Hardy.

I'm actually using scripts like wipet is but, there are various things you can do beyond what is at [www.lesswatts.org](www.lesswatts.org) (which is a great site) to lower power consumption.  Specifically, you can increase the ext3 journal commit interval and the dirty_writeback_centisecs to something on the order of several minutes.  That, combined with aggressive power savings with hdparm will allow your disk to mostly stay in standby mode for basic usage.  There are also nvidia specific things you can do but, those obviously won't help you.

---

### Post by nightfrost on 2008-05-10
> **vor said:**
> My power consumption with a T9300 (2.5Ghz), nvidia, LED display at 4/7, wifi on, compiz on, and common apps running is between 12.5W and 13W while relatively idle.  That's down from about the 18ish that I got by default in Hardy.

I'm actually using scripts like wipet is but, there are various things you can do beyond what is at [www.lesswatts.org](www.lesswatts.org) (which is a great site) to lower power consumption.  Specifically, you can increase the ext3 journal commit interval and the dirty_writeback_centisecs to something on the order of several minutes.  That, combined with aggressive power savings with hdparm will allow your disk to mostly stay in standby mode for basic usage.  There are also nvidia specific things you can do but, those obviously won't help you.

That's amazing! I don't think I've ever been that low on watts with wifi on. I got the 4965, believing that the new chip had better power saving abilities, but I'm starting to think otherwise.

Would you care to elaborate on the increased journal commit and the hdparm settings? Are you using -B or -S settings? And how many centisecs do you use?

I experimented a lot with hdparm saving feature on my old laptop, but never got it working very well. That machine didn't have a sata disk though, i don't know if that matters.

---

### Post by sdennie on 2008-05-10
Sure.  I'll just post the exact script that I use.  I call this script 99-savings.sh and put it in /etc/acpi/ac.d /etc/acpi/battery.d and (on Hardy) /usr/lib/pm-utils/power.d and /usr/lib/pm-utils/sleep.d:

```

#!/bin/bash

# Go fast.  More or less Ubuntu defaults
if on_ac_power; then
  hdparm -B 255 -S 240 -M 254 /dev/sda
  mount -o remount,commit=5 /
  mount -o remount,commit=5 /home
  echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
  echo 0 > /proc/sys/vm/laptop_mode
  echo 6 > /sys/bus/pci/drivers/iwl3945/0000\:0c\:00.0/power_level
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
  echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy
  echo max_performance > /sys/class/scsi_host/host2/link_power_management_policy
  echo userspace > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
  echo userspace > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
  echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
else # Save power
  hdparm -B 1 -S 4 -M 128 /dev/sda
  mount -o remount,commit=600 /
  mount -o remount,commit=600 /home
  echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
  echo 5 > /proc/sys/vm/laptop_mode
  echo 5 > /sys/bus/pci/drivers/iwl3945/0000\:0c\:00.0/power_level
  echo 40 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 30000 > /proc/sys/vm/dirty_writeback_centisecs
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
  echo min_power > /sys/class/scsi_host/host2/link_power_management_policy
  echo userspace > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
  echo userspace > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
  echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
fi

```

---

### Post by Axx83 on 2008-06-10
TO WIPET
Hi, I saw this post of yours:
> You should try the tips and tricks at this site: [http://www.lesswatts.org/](http://www.lesswatts.org/)
I made a script in /etc/acpi/battery.d that run every time I'm on battery with all those tips and I keep my consommation between 11 and 15 watts most of the time with a NVIDIA card (with the latest beta driver) on my m1330, with my brightness at 5/7, wifi on.

Well I would LOVE to have something that when I go in battery mode does all the things that powertop tells me without having to do them manually all the time. And of course when I plug the ac in they go back to normal. Is this what you did ? Could you help me do it too ? I'd write a good guide afterwards for everyone...Thanks ;-)

---

### Post by sdennie on 2008-06-10
> **Axx83 said:**
> TO WIPET
Hi, I saw this post of yours:


Well I would LOVE to have something that when I go in battery mode does all the things that powertop tells me without having to do them manually all the time. And of course when I plug the ac in they go back to normal. Is this what you did ? Could you help me do it too ? I'd write a good guide afterwards for everyone...Thanks ;-)

This link should get you started: [http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)

Though, I need to update it because I noticed that there are /etc/pm/sleep.d and /etc/pm/power.d.

---

### Post by Axx83 on 2008-06-10
That post looks good thanks !!! But I have a thinkpad and from what I know thinkpads use a version of acpi named differently, something like acpi-ibm of acpi-tp...am I correct ? Thanks anyway

---

### Post by sdennie on 2008-06-10
Thinkpads may use different kernel modules for various aspects of the acpi but, the acpi-support and pm-utils packages are applicable to any type of machine that has a working acpi.

---

### Post by Axx83 on 2008-06-10
Perfect, anyways...just to be very very very annoying, installing this script doesn't mess with the standard hardy configs like gnomepowermanager and all the governor stuff, and the fact that you are enabling laptopmode temporarily, and so on ?

I'm one of those not new neither experienced users who knows a lot of names but doesn't know how they really work eheheheheh

---

### Post by sdennie on 2008-06-10
The basic harness only takes advantage of the hooks that the acpi subsystem provides for adding user content so shouldn't have any negative effect.  The options that you add to that script could cause problems but, if you are more or less using powertop/lesswatts.org as a guide, you should be just fine.

---

### Post by Axx83 on 2008-06-10
Should I config laptop mode too ? Or is it just good now ?

By the way I should read that site more carefully and the guides at thinkwiki too, to make these scripts specific for my laptop, now without any of these my laptop lasts more or less 2 hours let's see how for it can get.

---

### Post by sdennie on 2008-06-10
laptop-mode is an alternate way of doing what that script does so, there is no need to use both.

---

### Post by Axx83 on 2008-06-10
But aren't you enabling laptopmode in that script when battery is on ? I'm confused

---

### Post by sdennie on 2008-06-10
There are two different things that are "laptop mode".  One is a program that does similar things to the script you are talking about, the other is a kernel tunable that basically tells the kernel to try to be smarter about how it does disk I/O.

---

### Post by Axx83 on 2008-06-10
Ok now I got it, thanks again !!! Your help has been fantastic, so what I basically need to do is turn off laptop mode tools I turned on some time ago, blindly following some other guide, if I haven't done that already, and try these scripts.

Do you happen to know how do I turn off this laptop mode automatic program ?

---

