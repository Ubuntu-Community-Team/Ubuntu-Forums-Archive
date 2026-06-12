---
title: "Sound Cuts Out At Low Volume (Inspiron 1525)"
date: 2011-09-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zjmichen on 2011-09-25
So I haven't found this topic elsewhere...

On my Inspiron 1525 I have two headphone jacks.  When I use either of these, and turn the volume relatively low (~16% on PulseAudio when ALSA is 100%, ~42% PA when ALSA is 25%), it just cuts out.

The weird thing is, it doesn't matter what I use to turn the volume down - PulseAudio and ALSA both make it cut out when I turn them down.  In fact, the PulseAudio volume meter never says it stops.

```
lspci
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```Any ideas on what the problem might be?  Any general audio device troubleshooting advice?

---

### Post by boneitis on 2011-10-03
+1.

Installed 64-bit Ubuntu 10.04 on my Inspiron 1520 a couple of weeks ago.  It was a horrifically painful process, having to mess around with so many things to get everything working right.  The only problems I have left now (besides a drastically increased boot time... any fix for this?) involve my sound.

Originally, my sound was actually fine, but in dealing with other issues, I uninstalled/reinstalled the alsa-base, alsa-utils, ubuntu-desktop, and linux-sound-base packages several times, and I now have a few side effects.

1) Same stuff as zjmichen above, and I have not bothered to try to figure out the exact percentages at which the cutout occurs, but his given figures sound about right.  If he did not explain the issue clearly enough, if we slowly slide the volume from 100% to 0%, everything works as expected from the 100% to 16ish%, but once it gets below that, there's no sound at all no matter where the slider is between that 0-16ish range. Quite inconvenient when a low volume is needed for headphones.

2) System bell.  I can't for the life of me disable it.  I've tried every method I could find with my Google Fu, but nothing works.  As is probably no surprise, it's VERY LOUD out of the speakers.  If headphones are plugged in (and sound not muted), it is, without exaggeration, so loud to the point of potential ear damage.  Here's a kicker: the system bell doesn't go off if I shutdown/reboot the computer shortly after booting up.  If the laptop's been on for a while and I've been doing stuff, I can pretty reliably count on the bell to go off.

I have tried:
- sudo modprobe -r pcspkr
- blacklist pcspkr added to /etc/modprobe.d/blacklist.conf
- install pcspkr /bin/true added to /etc/modprobe.d/blacklist.conf
- "Alert volume" in Sound Preferences > Sound Effects is both muted and at 0%

3) The alert sound thingy doesn't occur anymore.  For example, if I'm editing a file in vi, if I hold the 'j' key until it goes all the way to the bottom, then the cutesy alert sound should start going off.  Is there a setting for this?

All three issues arose at the same time for me.

Bueller?

---

### Post by zjmichen on 2011-10-03
Yeah that's exactly what happens.  I was beginning to think I was the only one with this problem!

Also boneitis, you didn't mention it, but have you tried muting the pc speaker in alsamixer?

---

### Post by boneitis on 2011-10-04
Worth a try.  Just installed it and muted it there.  Will find out after a while if it works.  Hard to tell right away, since it doesn't always occur.  Thanks!

---

### Post by boneitis on 2011-10-07
Well, looks like the system bell is finally done for.  Thank you!  Sound cutout thing still a problem though, for other readers.

---

### Post by boneitis on 2011-12-05
bumping

---

