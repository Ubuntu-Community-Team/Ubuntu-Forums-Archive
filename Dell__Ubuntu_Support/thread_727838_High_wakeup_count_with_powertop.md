---
title: "High wakeup count with powertop"
date: 2008-03-18
forum: Dell  Ubuntu Support
---

### Post by Superfish on 2008-03-18
I ran PowerTOP on my 1420N with Gutsy, and got this result:

Wakeups-from-idle per second : 884.9    interval: 10.0s
Power usage (ACPI estimate): 21.0W (1.8 hours) (long term: 26.6W,/1.5h)

Top causes for wakeups:
  64.8% (615.7)       <interrupt> : uhci_hcd:usb4, uhci_hcd:usb6, HDA Intel 
   6.6% ( 62.3)       <interrupt> : ahci, ipw3945, eth0 
   6.5% ( 61.7)       <interrupt> : nvidia 
   5.4% ( 50.9)       <interrupt> : extra timer interrupt 
   5.2% ( 49.9)   <kernel module> : cnxthsf_OsCreatePeriodicTimer (TimeOutHandle
   1.9% ( 18.2)       firefox-bin : futex_wait (hrtimer_wakeup) 

Is that an abnormally high number of uhci_hcd wakeups? I see some people with less than 100 wakeups total. How do I decrease this number?

One other thing - sometimes, the webcam on my laptop disappears - programs won't recognize it anymore. Could this be because of a power-saving feature?

Update: Removed uhci_hcd module, and it turns out that all those wakeups are from HDA Intel.

---

### Post by WanderingStar on 2008-03-18
Hey,

I also noticed a similar situation.  After reading around on this topic  it seemed like the drivers for the sound chip do not have any power management right now, so they are constantly running no matter if they are in use.  Source of that info is here: [http://www.lesswatts.org/tips/misc.php](http://www.lesswatts.org/tips/misc.php)

I'm not too concerned right now, as I find the battery life acceptable for my needs, and I'm hopeful that Hardy will improve things next month. 

WS

---

### Post by sciurus on 2008-03-18
That number seems high for me. Typing this message right now, I get around 250-350 wakeups per second. If i stop using the laptop, it drops to less than 200. I would get closer to 100 if I killed the wireless. Are you playing audio when this happens?

---

### Post by sdennie on 2008-03-18
You could try remove the sound module when you are on batteries.  Another thing you could try would be to download and build the latest alsa drivers (It's relatively straightforward actually).  That may or may not fix the problem but, it might be worth the effort.

You didn't ask about the other top wakeup things but, once you get past the sound problem, there are a few other things you can do to reduce wakeups.

> 
6.6% ( 62.3) <interrupt> : ahci, ipw3945, eth0


I don't know how many of these interrupts are coming from the wifi driver (I suppose you could test by physically turning the wifi radio off) but, with an intel 3945 card, using the iwl3945 driver usually gets me around 15 wakeups/sec.  In fact, Dell actually recommends using the iwl3945 driver instead of the ipw3945 driver: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)

> 
6.5% ( 61.7) <interrupt> : nvidia


You can get rid of almost all of these with a single configuration option in your xorg.conf.  See this thread: [http://ubuntuforums.org/showthread.php?t=694776](http://ubuntuforums.org/showthread.php?t=694776)

> 
5.2% ( 49.9) <kernel module> : cnxthsf_OsCreatePeriodicTimer (TimeOutHandle


I can't be certain but, I'm reasonably sure that this is caused by the modem driver.  If you aren't using the modem, you could remove the modem driver (I'm not certain what it's called) and that should get rid of these wakeups.

---

### Post by Superfish on 2008-03-19
Thanks a lot! I'll try some of these suggestions.

---

### Post by sdennie on 2008-03-19
Actually, now that I think about this some more, it's possible that the HDA Intel wakeups are related to the modem.  If you don't use it, I would see if you can disable it from the BIOS and see if that helps.

---

### Post by WanderingStar on 2008-03-20
I pulled the modem driver (not the modem itself mind you) and the wakeups continued.  I'm actually going to be moving to Hardy this weekend, and I'll report back if that makes any difference. 

WS.

---

### Post by sdennie on 2008-03-20
> **WanderingStar said:**
> I pulled the modem driver (not the modem itself mind you) and the wakeups continued.  I'm actually going to be moving to Hardy this weekend, and I'll report back if that makes any difference. 

WS.

Ok.  I have a Dell laptop that likely has the same sound card but, no modem.  Based on what you've posted, it looks like you have the Conexant HSF modem stuff installed and that's actually linked to the sound card.  Even while playing mp3s on battery power, I can't get the HDA Intel driver to wakeup more than ~50/sec (and there are essentially no wakeups if I'm not using the soundcard).

It's been a long time since I've dealt with conexant [junk] but, if I recall correctly, it installs a modified hda_intel driver.  I would try to completely disable the modem via BIOS and then download, build and install the latest alsa drivers.

A switch to Hardy would probably fix the problem because it would overwrite whatever changes the conexant driver has done but, if you want to stick with a more stable platform, simply undoing the conexant changes might work.  I don't know exactly how to go about removing the conexant packages and restoring things to the Gutsy defaults but, I have a feeling that doing so would kill those wakeups.

---

