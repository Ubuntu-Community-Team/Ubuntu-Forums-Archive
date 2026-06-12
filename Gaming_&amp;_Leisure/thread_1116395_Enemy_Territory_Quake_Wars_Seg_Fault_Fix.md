---
title: "Enemy Territory Quake Wars Seg Fault Fix"
date: 2009-04-04
forum: Gaming &amp; Leisure
---

### Post by SGAZ on 2009-04-04
I read a lot of threads in different forums about ETQW Segmentation Faults and frozen mice  -- pretty much because it was happening to me.  I never found any "Mine is fixed" threads so I figured I'd post one.

(For Me -- Ubuntu 8.10 & ATI SB sound hardware) The fix for seg faults and in game VOIP is to shutdown **pulseaudio** so the sound runs on ALSA only and then reset the mic device in my sound settings.  After that, the in game Options| Voice | "Test Sound" works. No more seg faults with VOIP/Voice chat button or keys.  The sound settings drop downs are all still blank but the TEST SOUND works.

**The process is:**
[INDENT](In Terminal)"killall pulseaudio".
(Reset/Set up mic)From the desktop: System | Preferences | Sound | Audio Conferencing - Sound Capture -- find the hardware device that you can hear your (unmuted) mic with when the TEST is running.

Use your mixer to fix up the clarity / volume issues with your mic after changing to Alsa.

Then do "Test Sound" in the game options.

To restart pusleaudio after ETQW (in Terminal) "pusleaudio -D" (-D starts the daemon) or just logoff and back on.  Put the mic device back to Pulseaudio in the sound setup if you need to.[/INDENT]

All that is a bummer because pulseaudio works pretty well with all my other apps. On the other hand, it only takes about 20 extra seconds to do (the second time).

If you don't want to mess with the mic and killing pulse audio you can prevent inadvertant (user caused) VOIP based seg faults by unbinding the Voice Chat keys in the Options |Controls | Misc. section of the game.  If you do this you can still seg fault your game if you click on a voice chat button in between maps!

Hope this helps somebody get to the having fun part quicker and with fewer interuptions.

---

### Post by RabidWeezle on 2009-08-23
Ahh, thank you very much. I think I will just make a script to killall -9 pulseaudio, run the game, then re-enable it :)

---

### Post by JillSwift on 2009-08-23
There's a program called "pasuspender" that does the same thing, but also lets pulse start back up on its own when you quit. Use it thus:

```
pasuspender /path/to/etqw
```

---

### Post by HTML-insane on 2009-09-03
Thanks! Having moved from Gentoo to Kubuntu just recently, I never thought that this might be caused by pulseaudio. I also removed it from all init runlevels, since I have absolutely no problems with Alsa and had no problems in Gentoo without pulseaudio. I'd like to know the command for removing init scripts from runlevels in the new init system, but I did the sloppy thing and used `rm /etc/rc*.d/pulseaudio` and `rm /etc/default/pulseaudio`.

---

