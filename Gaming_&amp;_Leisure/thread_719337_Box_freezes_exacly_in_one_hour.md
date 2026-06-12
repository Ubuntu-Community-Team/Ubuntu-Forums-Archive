---
title: "Box freezes exacly in one hour"
date: 2008-03-09
forum: Gaming &amp; Leisure
---

### Post by SR_ELPIRATA on 2008-03-09
Hello All:

Well, this is whats going on basically...

I start to play Open Arena, load one map with 2 bots and after one hour exactly, the full screen becomes window mode, the mouse and keyboard are locked and no key combination allows me to regain control of the computer.

Im using 7.10 and have a Ge FX5200. I got me Urban Terror, and so far been experiencing exactly the same behaviour. I check the time when I start playing and exactly one hour later the game goes to window mode, keyboard and mouse locked up.

I can rule out the sound because I have been playing without sound and a few hours ago I changed the sound systerm to PulseAudio and I still have exactly the same behavious.

Im not really sure where to start.... but only happens with 3d games (havent tried honestly a card game). Normal usage isnt affected at all, but when I load game I know that in one hour I'll be having a lockdown and I'll have to manually restart the computer.

Please, tell me there's hope...

ELP

Specs: Sempron 2400, 768MB DDR, Nforce2 Ultra Abit mobo NFS-7S (I think), Linux runs on a 40GB HDD.

---

### Post by jonnywombat on 2008-03-09
A couple of thoughts...

Have you checked to see if your screen saver is trying to kick in after1 hour. Also while in the screen saver settings check out the power options and make sure everything is set to never... 

There can be issues with screen saver/power settings thinking the machine is idle when gaming.. It happens to me in torcs....

Jonny

---

### Post by Cappy on 2008-03-09
wombat is correct, it is the screensaver.
```
killall gnome-screensaver
```
before playing or turn the screensaver completely off in the settings.

---

### Post by uDanimal on 2008-03-09
You might also check power management and make sure its not trying to go into hibernation/suspend/nappytime or whatever its called.   It would more than likely be a screensaver issue, but after that,  I would check the power management.

---

### Post by prshah on 2008-03-09
Open a terminal, and paste the output of the below command:

```

 cat /var/log/messages | grep MARK

```

Don't believe it to be a screensaver / power management issue since you seem to be using it while it locks.

Also, next time it locks up, try Ctrl+Alt+Shift+SysRq+E to terminate all programs. if that doesn't work, does Ctrl+Alt+Shift+SysRq+B instantly reboot the computer?

Cheers,
PRShah

---

### Post by SR_ELPIRATA on 2008-03-09
Thanks all for the replies.

I have to test it, but I can see that the Screensaver I had it set to 1 hour. The power management sections were set to never.

```
Mar  7 04:29:50 ThunderBolt -- MARK --
Mar  7 04:49:50 ThunderBolt -- MARK --
Mar  7 05:09:50 ThunderBolt -- MARK --
Mar  7 05:29:50 ThunderBolt -- MARK --
Mar  7 05:49:50 ThunderBolt -- MARK --
Mar  7 06:09:50 ThunderBolt -- MARK --
Mar  7 06:29:50 ThunderBolt -- MARK --
Mar  7 06:49:50 ThunderBolt -- MARK --
Mar  7 12:37:14 ThunderBolt -- MARK --
Mar  7 13:17:14 ThunderBolt -- MARK --
Mar  7 13:37:14 ThunderBolt -- MARK --
Mar  7 13:57:14 ThunderBolt -- MARK --
Mar  7 14:17:15 ThunderBolt -- MARK --
Mar  7 14:37:15 ThunderBolt -- MARK --
Mar  7 14:57:15 ThunderBolt -- MARK --
Mar  7 17:52:35 ThunderBolt -- MARK --
Mar  7 18:12:35 ThunderBolt -- MARK --
Mar  7 18:32:35 ThunderBolt -- MARK --
Mar  7 18:52:35 ThunderBolt -- MARK --
Mar  8 13:45:57 ThunderBolt -- MARK --
Mar  8 14:05:57 ThunderBolt -- MARK --
Mar  8 15:08:14 ThunderBolt -- MARK --
Mar  8 15:28:14 ThunderBolt -- MARK --
Mar  8 15:48:14 ThunderBolt -- MARK --
Mar  8 16:28:14 ThunderBolt -- MARK --
Mar  8 16:48:14 ThunderBolt -- MARK --
Mar  8 17:08:14 ThunderBolt -- MARK --
Mar  8 18:28:05 ThunderBolt -- MARK --
Mar  8 18:48:05 ThunderBolt -- MARK --
Mar  8 19:08:05 ThunderBolt -- MARK --
Mar  9 00:40:04 ThunderBolt -- MARK --
Mar  9 01:26:45 ThunderBolt -- MARK --
Mar  9 01:46:45 ThunderBolt -- MARK --
Mar  9 02:06:45 ThunderBolt -- MARK --
Mar  9 02:33:54 ThunderBolt -- MARK --
Mar  9 02:53:54 ThunderBolt -- MARK --
Mar  9 03:13:54 ThunderBolt -- MARK --
Mar  9 03:36:29 ThunderBolt -- MARK --
Mar  9 03:56:29 ThunderBolt -- MARK --
Mar  9 04:16:29 ThunderBolt -- MARK --
Mar  9 04:38:54 ThunderBolt -- MARK --
Mar  9 04:58:54 ThunderBolt -- MARK --
Mar  9 05:18:54 ThunderBolt -- MARK --
```

Not sure what u can do with this... but by all means :)

Gonna get in-game and see what happens.. thanks all.

ELP

---

### Post by SR_ELPIRATA on 2008-03-09
Ok, no lockups anymore. Thanks all.

Out of curiousity..

Ctrl+Alt+Shift+SysRq+E

Which is the SysRq button? Do I have to press them all together or in sequence...

ELP

---

### Post by Cappy on 2008-03-09
It's Alt + SysRq (PrintsScreen button) + key

You press them all at the same time.

You can see all key combinations here:
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

