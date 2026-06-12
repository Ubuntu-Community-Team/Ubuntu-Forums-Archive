---
title: "help with diagnosing system freeze"
date: 2009-01-13
forum: General Help
---

### Post by sonnenwende93 on 2009-01-13
I have Ubuntu 8.10 64-bit on a new computer and am having a recurring problem where the system will randomly freeze up, usually when I click on a window or perform some other action. It doesn't seem to matter what program I am using. 

I can still move the mouse, and if I am playing music it will keep going, but X is totally locked and I can't ctrl+alt+backspace, or crtl+F#.

The only way to restart is by holding the power switch (I tried alt+sysrq too).

After rebooting I can't find anything in any of the system logs that makes any sense to me or gives any hints. I ran memtest86 for an hour or so as well.

Any ideas how to start narrow this down?

---

### Post by 2hot6ft2 on 2009-01-13
Since you didn't mention the graphics card there are these 2.

System Freezes
Ubunut Intrepid - Clocksource From Hell
[http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubunut-intrepid-clocksource-from-hell](http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubunut-intrepid-clocksource-from-hell)

Ubuntu Intrepid - Clocksource Fixed, System Still Hangs, AND No Videos - FGRLX Fixes It
[http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubuntu-intrepid-clocksource-fixed-system-still-hangs-and-no-videos-fgrlx-f](http://my.opera.com/PiklesOnFire/blog/2008/12/07/ubuntu-intrepid-clocksource-fixed-system-still-hangs-and-no-videos-fgrlx-f)

 and
Believe it or not some freezes seem to tie into the sound Pulse Audio (when not configured properly) can send the cpu to 100% causing the freeze. This has been reported by several people and the solution is here for that.
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

I was having freezes too and since completing the how to have not had a freeze at all.

This may or may not be your particular issue but it's where I would start after reading everything I have.

There's a start for you.

---

### Post by sonnenwende93 on 2009-01-14
Thanks, I forgot to mention it's an onboard nvidia GPU. I figure it must be related to the graphics in some way because the audio was till going and xorg was locked up. 

Actually - as I was typing this it locked up again. The only thing I see is the system log is this - which is when it froze up:

```
Jan 14 00:11:33 HIVE kernel: [13520.090858] NVRM: Xid (0002:00): 13, 0001 00000000 0000502d 0000060c 000000e5 00000100
Jan 14 00:11:33 HIVE kernel: [13520.143844] NVRM: Xid (0002:00): 13, 0001 00000000 0000502d 000008dc 00000000 00000100
Jan 14 00:11:37 HIVE kernel: [13524.081633] NVRM: Xid (0002:00): 13, 0003 00000000 00008397 00001408 00000001 00000040
Jan 14 00:11:37 HIVE kernel: [13524.813492] NVRM: Xid (0002:00): 13, 0003 00000000 00008397 00001310 00000000 00000040
Jan 14 00:11:38 HIVE kernel: [13525.755857] NVRM: Xid (0002:00): 13, 0003 00000000 00008397 00001310 00000000 00000040
Jan 14 00:11:43 HIVE kernel: [13530.624246] NVRM: Xid (0002:00): 13, 0003 00000000 00008397 00001310 00000000 00000040
Jan 14 00:11:47 HIVE kernel: [13534.189758] NVRM: Xid (0002:00): 13, 0003 00000000 00008397 00001310 00000000 00000040
Jan 14 00:11:54 HIVE kernel: [13541.447446] NVRM: Xid (0002:00): 13, 0003 00000000 00008397 00001310 00000000 00000040
```

Looks like this shows up on all the occasions it has done this. I checked out the thing about hpet, but that doesnt look like its the problem for me, and as an nvidia user i know it's not FGLRX (and I updated the the latest nvidia driver). Im going to try the fixes in the Pulse audio thread and see if that helps. Thanks.

---

### Post by ppmt on 2009-03-18
I am going to revive this topic

I have exactly the same problem since I replace my motherboard

it has a integrated Nvidia 8200 and it freeze randomly with the same printout

What I noticed is that it seems related to Compiz. If I disable Compiz I have no freeze 

But I like my Compiz :(

Also when I had an standalone nvidia 7600GT I never had that problem.

---

### Post by screig on 2009-06-15
ASUS P5N7A-VM with integrated NVIDIA 9300

Jun 15 20:07:20 NightFlyer NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Jun 15 20:07:20 NightFlyer NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Jun 15 20:07:20 NightFlyer ntpdate[4114]: adjust time server 91.189.94.4 offset 0.433523 sec
Jun 15 20:07:26 NightFlyer kernel: [   54.536036] wlan0: no IPv6 routers present
Jun 15 20:08:36 NightFlyer kernel: [  123.868071] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 00000104 00000000 00000100
Jun 15 20:08:36 NightFlyer kernel: [  123.884637] NVRM: Xid (0003:00): 13, 0003 00000000 00008397 00001408 00000001 00000040
Jun 15 20:08:37 NightFlyer kernel: [  124.945726] NVRM: Xid (0003:00): 13, 0003 00000000 00008397 000015e0 00000000 00000040
Jun 15 20:08:37 NightFlyer kernel: [  124.960615] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 00000104 00000000 00000100
Jun 15 20:08:37 NightFlyer kernel: [  125.106931] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 00000104 00000000 00000100
Jun 15 20:09:53 NightFlyer syslogd 1.5.0#5ubuntu3: restart.
Jun 15 20:09:53 NightFlyer kernel: Inspecting /boot/System.map-2.6.29-020629-generic
Jun 15 20:09:53 NightFlyer kernel: Cannot find map file.
Jun 15 20:09:53 NightFlyer kernel: Loaded 82768 symbols from 52 modules.
Jun 15 20:09:53 NightFlyer kernel: [    0.000000] Initializing cgroup subs

...s**t

---

### Post by mishaokami on 2009-08-04
I've had the same experience with my nvidia 9300/730i.
I would doubt that the problem is with compiz.  My experience is this:

I use nvidia 180 from the repos

Turn on compiz (and thereby the compositor) = crash or on a good day Xorg (nvidias user space X binary) goes to 100%

Turn off compiz and turn on metacitys compositor = same

Turn off both compositors and im stable.

That is alot of suck.
Unfortunately it looks like nvidias own closed source xclient or kernel drivers are suspect.  I'm not quite sure where this functionality is coded.

This said, i have not as yet tried to use blender or something else that stresses other features of the chip.  Perhaps all 3d stuff is a loss.

m

---

