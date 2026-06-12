---
title: "Strange desktop behavior when one external HD automounts"
date: 2012-11-09
forum: Desktop Environments
---

### Post by ray field on 2012-11-09
I have three external USB drives attached to my desktop computer. One of them used to be attached as an eSATA drive, until I got tired of its flakey behavior (couldn't rely on it to run backup scripts, because it wouldn't reliably wake up in the middle of the night) so I switched it to USB, where it has been working fine, EXCEPT:

If I boot with it turned on, my Unity 3D desktop settings are lost -- the font, theme, and icons are all generic. Applications and applets all load, however. Also, none of my system settings can be retained -- for instance, I prefer to switch mouse buttons, but in this state, Unity won't switch them. I just checked, and although the "left-handed mouse" radio button was ticked, the mouse doesn't actually behave that way. And -- I hate the way the desktop looks.

As a result, when I reboot -- which alas, is about once a day thinks to Unity's instability -- I have to remember to shut off the external drive before the power cycle starts up again. Since I only remember to do this about half the time, I seem to waste a few minutes every day on this. Is this a bug or a feature I don't understand?  How can I get my installation to start up normally with that drive automounted?

---

### Post by 2F4U on 2012-11-09
What version of Ubuntu are you using?

---

### Post by ray field on 2012-11-09
> **2F4U said:**
> What version of Ubuntu are you using?

12.04 (with all the latest updates)

---

### Post by ray field on 2012-11-11
> **ray field said:**
> 12.04 (with all the latest updates)

and here is something struck me as strange: I don't particularly want to try out Quantal, but since Compiz is such a mess in Precise I thought to give it a try...

...and found the SAME, EXACT behavior as for Precise: with this particular external HD attached, I cannot save desktop settings, however once I've unmounted it and turned it off and rebooted, my desktop opens and behaves normally. 

maybe someone understands this. weird.

---

### Post by ray field on 2012-11-14
bbuuummp

---

### Post by cjhabs on 2012-11-14
Do you have an OS on that external drive - is the system booting from that drive instead of the usual drive? I have an external that has grub and various OS loaded on it and the system will default to one of the OS on that when it is connected at boot time - I have a delay on the grub screen so I can select the OS i want - your may be jumping straight to it. You can check by running "df" and seeing what partition was mounted as the root.
Just a thought

---

### Post by ray field on 2012-11-14
thanks -- just (re)checked, and -- no, it's just massively filled with tarred backups, remastersys ISOs, and miscellaneous flotsam & jetsam. 

I wonder if it's just this model -- mabye something about the way it connects to the USB bus conflicts with like the mouse or something? sure would like to know cause it's sort of a weird pita.

---

