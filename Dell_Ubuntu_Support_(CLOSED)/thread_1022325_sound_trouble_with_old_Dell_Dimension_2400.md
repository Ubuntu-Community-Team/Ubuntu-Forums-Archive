---
title: "sound trouble with old Dell Dimension 2400"
date: 2008-12-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by stompr on 2008-12-26
Hey people, I need some extra minds to help me figure out a problem I'm having getting a Dell Dimension 2400 to play music, under Xubuntu, out it's integrated sound device.  So far:

The modules load OK (OK meaning that it doesn't spit out errors, and the modules show in the output of lsmod).

Alsamixer sees all the available channels.

After restarting the alsa server, the volume control in the system tray disappeared and fails to show back up.  This is after trying to add a volume control object to the top pannel in an attempt to correct the problem.

I installed the pulseaudio packages, and reinstalled the linux-sound-base and all associated alsa packages with no effect.

I will be able to provide any information you need.  All you have to do is ask for it, with the command needed to display it.

Thanks guys.

---

### Post by stompr on 2008-12-27
I fixed the problem by adding a new sound card I had kicking around and disabling the onboard sound device.  Apparently it was a big IRQ conflict between that and the onboard NIC that couldn't be resolved otherwise with what I knew off hand.  I hope this helps anyone else with the same problems with the same computer.

If anyone has any ideas on how to get the onboard sound functioning, feel free to throw them around, but it's not important to me anymore.  It'll just make me feel less like a cop-out that runs around screaming "Hey guys, I need help here with this super-hard problem... aw nevermind, I found  way to get past it by not addressing it!"

---

### Post by Ompsksch on 2008-12-29
Yes! I have a volume issue with my Dell 2400. I have no volume control; it runs at full volume. Any tips here? Thanks in advance...

---

