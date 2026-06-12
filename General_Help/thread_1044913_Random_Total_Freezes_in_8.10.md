---
title: "Random Total Freezes in 8.10"
date: 2009-01-19
forum: General Help
---

### Post by Technogenius on 2009-01-19
I am dual-booting Ubuntu and XP. This problem only exists in Ubuntu, so I know it isn't a hardware fault. Ubuntu will completely freeze at random. By "completely freeze" I mean not even CTRL+ALT+F1 does anything. If I reset my computer and reboot, I will see a copy of the screen that was frozen flash briefly before the login window. Any help would be appreciated, as this is getting pretty annoying.

---

### Post by Yashiro on 2009-01-19
Probably an issue with the video driver.

---

### Post by Pahanilmanlintu on 2009-01-20
I've been having a very similar problem since the day Hardy was released. I installed it right away, but it froze the first time during installation. It's been going on since then. I upgraded to Intrepid when it was released, but it didn't affect this issue.

There's slight variation in how it happens. Usually i notice it from the music or mouse pointer stopping. Nothing works and nothing happens. But a couple of times the currently playing song (on Exaile) has played through.

It happens with or without compiz, and often during the boot process or login. I've never found anything interesting in logs afterwards, but it's entirely possible that i just don't recognize it. Kern.log often (maybe always? I don't know) has these the last thing before freeze:

```
Jan 20 08:23:26 mustikki kernel: [  125.781630] ppdev0: registered pardevice
Jan 20 08:23:26 mustikki kernel: [  125.829352] ppdev0: unregistered pardevice
Jan 20 08:23:27 mustikki kernel: [  125.941209] ppdev0: registered pardevice
Jan 20 08:23:27 mustikki kernel: [  125.989075] ppdev0: unregistered pardevice
Jan 20 08:23:29 mustikki kernel: [  128.296645] ppdev0: registered pardevice
Jan 20 08:23:29 mustikki kernel: [  128.344571] ppdev0: unregistered pardevice
```

I don't know what exactly should i be looking for, but around the time of the freeze, syslog looks like this:

```
Jan 20 08:22:13 mustikki pulseaudio[5594]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Jan 20 08:22:23 mustikki kernel: [   62.694423] UDF-fs: Partition marked readonly; forcing readonly mount
Jan 20 08:22:23 mustikki kernel: [   62.722919] UDF-fs INFO UDF: Mounting volume 'Oblivion', timestamp 2006/03/01 01:58 (1078)
Jan 20 08:23:26 mustikki kernel: [  125.781630] ppdev0: registered pardevice
Jan 20 08:23:26 mustikki python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Jan 20 08:23:26 mustikki kernel: [  125.829352] ppdev0: unregistered pardevice
Jan 20 08:23:27 mustikki kernel: [  125.941209] ppdev0: registered pardevice
Jan 20 08:23:27 mustikki kernel: [  125.989075] ppdev0: unregistered pardevice
Jan 20 08:23:29 mustikki kernel: [  128.296645] ppdev0: registered pardevice
Jan 20 08:23:29 mustikki hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Jan 20 08:23:29 mustikki kernel: [  128.344571] ppdev0: unregistered pardevice
Jan 20 08:26:45 mustikki anacron[5285]: Job `cron.daily' started
Jan 20 08:26:45 mustikki anacron[5957]: Updated timestamp for job `cron.daily' to 2009-01-20
Jan 20 08:31:45 mustikki syslogd 1.5.0#2ubuntu6: restart.
Jan 20 08:31:46 mustikki kernel: Inspecting /boot/System.map-2.6.27-9-generic
Jan 20 08:31:46 mustikki kernel: Cannot find map file.
Jan 20 08:31:46 mustikki kernel: Loaded 65738 symbols from 79 modules.
Jan 20 08:31:46 mustikki kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 20 08:31:46 mustikki kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 20 08:31:46 mustikki kernel: [    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
Jan 20 08:31:46 mustikki kernel: [    0.000000] Command line: root=UUID=1323f37f-3371-4fd6-938c-3739a6420f00 ro quiet splash 
Jan 20 08:31:46 mustikki kernel: [    0.000000] KERNEL supported cpus:
Jan 20 08:31:46 mustikki kernel: [    0.000000]   Intel GenuineIntel
Jan 20 08:31:46 mustikki kernel: [    0.000000]   AMD AuthenticAMD
Jan 20 08:31:46 mustikki kernel: [    0.000000]   Centaur CentaurHauls
```

Didn't look at the time but i think it froze around 8:31. I also dual boot winXP which doesn't have problems. Oh, and the ***Caps Lock doesn't blink***.

edit: i got nvidia 8800gt with the newest nvidia driver in repos, amd x2 3800+, 2 gigs of ram, 500GB western digital on sata, 64-bit intrepid, compiz in use, LG dvd drive (that spins loudly for 5 mins after booting... argh), asus motherboard with something like nforce4 etc.

---

### Post by Technogenius on 2009-01-20
I am just using the nv driver for now, since I haven't got around to installing the NVidia drivers. My caps lock light seems to be working fine. I also looked at kern.log and I don't have any of the entries you had. One thing I do notice is an unregistered resource on boot. Ubuntu self-suggests it's a kernel bug.

---

### Post by jhend on 2009-01-20
I've been having the same problem. The Caps lock light will start blinking and nothing will move. The screen freezes and if I close the lid it won't go into suspend. All I can do is turn it off and turn it back on. Any ideas?

---

### Post by Technogenius on 2009-01-20
This has happened with two GeForce 6600GT's and the 177 driver and with two GeForce 9800GT's with the nv driver. The thing that confuses me is the frozen screen popping up for a split second after a hard reset. Does Xorg store the screen's contents on the hard drive?

---

