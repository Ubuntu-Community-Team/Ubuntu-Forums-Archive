---
title: "Natty: system freeze when using xvnc4viewer on Thinkpad X220"
date: 2011-05-29
forum: Desktop Environments
---

### Post by jeorsch on 2011-05-29
Hi,

I just installed Ubuntu Natty on my new Thinkpad X220 two weeks ago. I use VNC quite often to connect to a remote desktop via a double ssh tunnel. It uses to work well, but three or four times I had a total system freeze when using VNC in fullscreen mode. When I say total I mean total: no caps lock LED, no wireless hardware switch, and no mouse cursor working anymore. Only thing that is still functional is the mute LED, but this does not necessarily indicate Ubuntu's mute status anyhow. BTW: It would be nice if this could be fixed. Only powering off and on again helps. Logs do not contain anything unusual.
Of cause this could be a hardware problem, but it only happend when using VNC in fullscreen mode so far. Everything else including Windows 7 works perfect, so it is probably software induced in my opinion. Also tried to bump to the most current BIOS release (1.15), but it did not help.
I had WLAN on, Bluetooth off, power supply attached, USB mouse attached, "acpi_osi=linux" added to grub.cfg.
EDIT: I just ran MemtestX86+ V4.20 (V4.10 does not support Sandy Bridge). No errors.

Any suggestions?

Thanks!

Georg

---

### Post by joee92 on 2011-10-12
I too have occasional hard freezes on my new X220.  Seemingly random timing, but averages about one every other day.

**Same as jeorsch**: no caps lock LED; no mouse cursor; WLAN on; Bluetooth off; power supply attached; Windows 7 has never crashed (though I've only used it maybe an hour or two); memtest86+ ran for about 6 hours with no problems detected; latest BIOS from Lenovo

**Different**: oneiric beta (kernel 3.0.0-12); not always with external USB mouse attached; not using vnc (it's not even installed); no acpi_osi=linux

I haven't tried the wireless hardware switch or the mute switch (but I will, next time it locks up).  I have installed an extra 4GB of RAM (8 total).  There's nothing notable in syslog at the time of the crash.

---

### Post by TopicMapper333 on 2011-10-13
I'm having the same sudden freezing problem (natty, Lenovo X220), but I'm not necessarily running a VNC viewer when the crash occurs.  It usually happens when I'm actually using the machine, but not always.  Mozilla is always running, in case that means anything, which it probably doesn't.  It looks like some kind of device driver problem to me, perhaps one involving the display hardware.  Hard to say, given the lack of any indication in the logs.

Only fix is to power off and reboot.  The machine goes completely offline, ignoring all keypresses and all attempts to log in via ssh from elsewhere.  :icon_frown:

---

