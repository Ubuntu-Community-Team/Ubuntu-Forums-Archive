---
title: "Enabling internal speaker?"
date: 2011-01-10
forum: Desktop Environments
---

### Post by mma8x on 2011-01-10
Running 10.10 off a usb drive.  Previously using 10.04, didn't have a problem running sound off of the computer's internal speaker.  Now it will play out of the audio out jack, but not the internal speaker.  My only output option is "Internal Audio Analog Stereo".

lspci -v:

```
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Device 3034
        Flags: bus master, fast devsel, latency 0, IRQ 48
        Memory at f0520000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


```  

Thanks!

---

### Post by ankspo71 on 2011-01-12
Hi,
Are you referring to the system beep? Or actual built in speakers (like the speakers in a laptop)?

If you are referring to the system beep...then when you plugged in your speakers the "pcspkr" probably got blacklisted from starting automatically, or it got muted. I think some versions of ubuntu/kubuntu might have it blacklisted by default too. I am using desktop speakers, and my "pcspkr" is currently blacklisted. Have a look at this link: [http://superuser.com/questions/22767/enable-system-beep-in-ubuntu](http://superuser.com/questions/22767/enable-system-beep-in-ubuntu)

You can also adjust system notifications/sounds at: System Settings > Application and System Notifications > Manage Notifications.

As far as regular built in speakers go, I don't have any idea (sorry).

---

### Post by mma8x on 2011-01-12
well, not sure what the issue was.  i was trying to enable sound through the pc's internal speaker, since these are work computers without external speakers that plug into the "audio out" ports.  Anyway, I enabled pcspkr module as outlined above (though the file was "blacklist.conf").  However, I also unmuted the "mono" and "front" sliders in alsamixer--I had tried this before, but for some reason, it kept re-muting it.  I think that was the culprit, but I'm too lazy to reboot at the moment.  I re-blacklisted pcspkr--if that turns out to be the culprit, i'll update.  Otherwise, assume that the alsa manipulations did it.  Strange (and confusing) that this can't be done through kmix.

---

### Post by micheldell on 2011-01-12
If the desktop does not have a sound card or built-in voice, how to make the speakers inside the casing, so it will not only beep code (hint you just turn the power on) function. I see a lot of the desktop, internal speakers concurrently the main speakers.

---

### Post by ankspo71 on 2011-01-12
Here's another link that concerns using the little internal speaker built into the motherboards. [http://www.uluga.ubuntuforums.org/showthread.php?t=1490771](http://www.uluga.ubuntuforums.org/showthread.php?t=1490771)

---

### Post by mma8x on 2011-01-14
blacklisting had nothing to do with my problem--i changed all the blacklist settings back to default, kept the alsamixer changes, and i still have sound.

---

