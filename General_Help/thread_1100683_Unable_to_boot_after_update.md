---
title: "Unable to boot after update"
date: 2009-03-19
forum: General Help
---

### Post by uvdevnull on 2009-03-19
Running 8.04 Server
The following updates were installed this morning:
```
	dash 0.5.4-8ubuntu1.1
	libcurl3 7.18.0-1ubuntu2.1
	libcurl3-gnutls 7.18.0-1ubuntu2.1
	libglib2.0-0 2.16.6-0ubuntu1.1
	libglib2.0-data 2.16.6-0ubuntu1.1
	libpng12-0 1.2.15~beta5-3ubuntu0.1
	libxen3 3.2.0-0ubuntu10.1
	python-xen-3.2 3.2.0-0ubuntu10.1
	tzdata 2009b-0ubuntu0.8.04
	xen-docs-3.2 3.2.0-0ubuntu10.1
	xen-hypervisor-3.2 3.2.0-0ubuntu10.1
	xen-utils-3.2 3.2.0-0ubuntu10.1
```

Now I can't boot into the normal kernel (2.6.24-23-server), only recovery.

The startup process gets pretty far into it, including initialization of networking.  The last thing I see is:
```
* Running local boot scripts (/etc/rc.local)  [OK]
```
Then it just hangs there indefinitely.

Where do I start troubleshooting?  I'm fairly new to linux.

Thanks guys,
uv

---

### Post by HermanAB on 2009-03-19
You should look at the log files /var/log/messages for example, to see what happened.

However, you will likely have to re-install the system to get it going again.  Provided that your data is in a separate /home partition re-installing is quick and painless.  Then, once working, don't fix it if it ain't broken and turn automatic updates off.  Linux is incredibly stable and can run for years without problems.  

In my experience, more problems are caused by updates, than are fixed by them, especially if you have a moderately complex setup with virtualization (KVM) or various servers running.  Updates are well intentioned, but on a simple system you don't need them and on a complex system, it breaks things, so you should not apply updates without testing them first on a separate system.

Just my tuppence worth!

Herman

---

### Post by uvdevnull on 2009-03-19
> **HermanAB said:**
> 
However, you will likely have to re-install the system to get it going again.  Provided that your data is in a separate /home partition re-installing is quick and painless.  

Reconfiguring all the settings, reinstalling apps, etc... All that doesn't really make me think "quick" :)

---

### Post by fieroboom on 2009-03-19
> **HermanAB said:**
> You should look at the log files /var/log/messages for example, to see what happened.

However, you will likely have to re-install the system to get it going again.  Provided that your data is in a separate /home partition re-installing is quick and painless.  Then, once working, don't fix it if it ain't broken and turn automatic updates off.  Linux is incredibly stable and can run for years without problems.  

In my experience, more problems are caused by updates, than are fixed by them, especially if you have a moderately complex setup with virtualization (KVM) or various servers running.  Updates are well intentioned, but on a simple system you don't need them and on a complex system, it breaks things, so you should not apply updates without testing them first on a separate system.

Just my tuppence worth!

Herman

I disagree with this. Updates are there for a reason, or else there would be no LTS versions. Also, reinstalling isn't really troubleshooting the issue. I'm not trying to be an A-hole, but it sounds like the OP would rather TS than reinstall...

uvdevnull, here is what I would do... Edit /etc/default/bootlogd and turn on boot message logging:
```
sudo nano /etc/default/bootlogd
``` 

Nano will open, and the following will show:

```

# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No

```

Change BOOTLOGD_ENABLE to yes, and it will create /var/log/boot upon reboot, and you'll be able to see what you see on the screen during boot time. Then, you can also check /var/log/messages, /var/log/dmesg, and /var/log/syslog
Dmesg will probably be the most promising, since it's a rolling buffer that starts before any of the log files get initiated, but checking all 4 of those logs will most likely clue you in:
```
cat /var/log/boot

tail -n 50 /var/log/messages

tail -n 50 /var/log/dmesg

tail -n 50 /var/log/syslog
```

Since it's initializing networking, the easiest way to capture those errors is probably going to be to SSH to it (you should be able to, if I remember correctly) and run the above commands, then post them here.
Knowing where to look is half the battle... ;)
:D
-Paul

---

### Post by uvdevnull on 2009-03-19
Thanks Paul for you reply and attempt to troubleshoot this with me. I certainly appreciate it a lot. I've been a Windows admin for many years and feel comfortable there, but this a new world for me and not even knowing where log files are located sucks :)

Ok, so I was able to SSH into the server even when the console boot doesn't seem to complete.  However, nothing in bootlogd:
```
[devvm1: ~]$ cat /etc/default/bootlogd
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes
[devvm1: ~]$ cat /var/log/boot
(Nothing has been logged yet.)

```
Here are the other logs:
```
[devvm1: ~]$ tail -n 50 /var/log/messages
Mar 19 14:05:09 devvm1 kernel: [  101.483001] scsi 3:0:0:0: Direct-Access     ATA      Maxtor 6Y160M0   YAR5 PQ: 0 ANSI: 5
Mar 19 14:05:09 devvm1 kernel: [  101.501272] Driver 'sr' needs updating - please use bus_type methods
Mar 19 14:05:09 devvm1 kernel: [  101.509258] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
Mar 19 14:05:09 devvm1 kernel: [  101.509264] Uniform CD-ROM driver Revision: 3.20
Mar 19 14:05:09 devvm1 kernel: [  101.510219] Driver 'sd' needs updating - please use bus_type methods
Mar 19 14:05:09 devvm1 kernel: [  101.515510] sd 3:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
Mar 19 14:05:09 devvm1 kernel: [  101.515538] sd 3:0:0:0: [sda] Write Protect is off
Mar 19 14:05:09 devvm1 kernel: [  101.515581] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 19 14:05:09 devvm1 kernel: [  101.515674] sd 3:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
Mar 19 14:05:09 devvm1 kernel: [  101.515697] sd 3:0:0:0: [sda] Write Protect is off
Mar 19 14:05:09 devvm1 kernel: [  101.515739] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 19 14:05:09 devvm1 kernel: [  101.515744]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
Mar 19 14:05:09 devvm1 kernel: [  101.517369] sd 3:0:0:0: Attached scsi generic sg1 type 0
Mar 19 14:05:09 devvm1 kernel: [  101.528613]  sda1 sda2 < sda5 >
Mar 19 14:05:09 devvm1 kernel: [  101.553806] sd 3:0:0:0: [sda] Attached SCSI disk
Mar 19 14:05:09 devvm1 kernel: [  108.145025] Attempting manual resume
Mar 19 14:05:09 devvm1 kernel: [  108.167282] EXT3-fs: INFO: recovery required on readonly filesystem.
Mar 19 14:05:09 devvm1 kernel: [  108.167287] EXT3-fs: write access will be enabled during recovery.
Mar 19 14:05:09 devvm1 kernel: [  108.229560] kjournald starting.  Commit interval 5 seconds
Mar 19 14:05:09 devvm1 kernel: [  108.229580] EXT3-fs: recovery complete.
Mar 19 14:05:09 devvm1 kernel: [  108.230168] EXT3-fs: mounted filesystem with ordered data mode.
Mar 19 14:05:09 devvm1 kernel: [  112.886413] input: PC Speaker as /devices/platform/pcspkr/input/input2
Mar 19 14:05:09 devvm1 kernel: [  112.918514] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 19 14:05:09 devvm1 kernel: [  113.008313] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 19 14:05:09 devvm1 kernel: [  113.108279] EDAC MC: Ver: 2.1.0 Jan 26 2009
Mar 19 14:05:09 devvm1 kernel: [  113.167877] iTCO_vendor_support: vendor-support=0
Mar 19 14:05:09 devvm1 kernel: [  113.217775] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Mar 19 14:05:09 devvm1 kernel: [  113.217892] iTCO_wdt: Found a 6300ESB TCO device (Version=1, TCOBASE=0x0860)
Mar 19 14:05:09 devvm1 kernel: [  113.217935] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Mar 19 14:05:09 devvm1 kernel: [  113.277704] EDAC i82875p: i82875p init one
Mar 19 14:05:09 devvm1 kernel: [  113.278022] EDAC MC0: Giving out device to 'i82875p_edac' 'i82875p': DEV 0000:00:00.0
Mar 19 14:05:09 devvm1 kernel: [  113.278056] EDAC PCI0: Giving out device to module 'i82875p_edac' controller 'EDAC PCI controller': DEV '0000:00:00.0' (POLLED)
Mar 19 14:05:09 devvm1 kernel: [  113.357512] Intel 82802 RNG detected
Mar 19 14:05:09 devvm1 kernel: [  113.387561] input: Power Button (FF) as /devices/virtual/input/input3
Mar 19 14:05:09 devvm1 kernel: [  113.427326] ACPI: Power Button (FF) [PWRF]
Mar 19 14:05:09 devvm1 kernel: [  113.427448] input: Power Button (CM) as /devices/virtual/input/input4
Mar 19 14:05:09 devvm1 kernel: [  113.432863] Linux agpgart interface v0.102
Mar 19 14:05:09 devvm1 kernel: [  113.467230] ACPI: Power Button (CM) [PWRB]
Mar 19 14:05:09 devvm1 kernel: [  113.467337] input: Sleep Button (CM) as /devices/virtual/input/input5
Mar 19 14:05:09 devvm1 kernel: [  113.507161] ACPI: Sleep Button (CM) [SLPB]
Mar 19 14:05:09 devvm1 kernel: [  114.555330] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
Mar 19 14:05:09 devvm1 kernel: [  114.705002] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Mar 19 14:05:09 devvm1 kernel: [  116.112452] NET: Registered protocol family 17
Mar 19 14:05:09 devvm1 kernel: [  119.202503] loop: module loaded
Mar 19 14:05:09 devvm1 kernel: [  119.252184] lp: driver loaded but no devices found
Mar 19 14:05:09 devvm1 kernel: [  119.546177] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
Mar 19 14:05:09 devvm1 kernel: [  119.865299] EXT3 FS on sda1, internal journal
Mar 19 14:05:09 devvm1 kernel: [  120.685130] NET: Registered protocol family 10
Mar 19 14:05:09 devvm1 kernel: [  120.685453] lo: Disabled Privacy Extensions
Mar 19 14:05:09 devvm1 kernel: [  121.717325] ip_tables: (C) 2000-2006 Netfilter Core Team

```
```
[devvm1: ~]$ tail -n 50 /var/log/dmesg
[  101.515510] sd 3:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[  101.515538] sd 3:0:0:0: [sda] Write Protect is off
[  101.515541] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  101.515581] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  101.515674] sd 3:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[  101.515697] sd 3:0:0:0: [sda] Write Protect is off
[  101.515700] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  101.515739] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  101.515744]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[  101.517369] sd 3:0:0:0: Attached scsi generic sg1 type 0
[  101.528613]  sda1 sda2 < sda5 >
[  101.553806] sd 3:0:0:0: [sda] Attached SCSI disk
[  108.145025] Attempting manual resume
[  108.145031] swsusp: Resume From Partition 8:5
[  108.145033] PM: Checking swsusp image.
[  108.145334] PM: Resume from disk failed.
[  108.167282] EXT3-fs: INFO: recovery required on readonly filesystem.
[  108.167287] EXT3-fs: write access will be enabled during recovery.
[  108.229560] kjournald starting.  Commit interval 5 seconds
[  108.229580] EXT3-fs: recovery complete.
[  108.230168] EXT3-fs: mounted filesystem with ordered data mode.
[  112.886413] input: PC Speaker as /devices/platform/pcspkr/input/input2
[  112.918514] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  113.008313] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  113.108279] EDAC MC: Ver: 2.1.0 Jan 26 2009
[  113.167877] iTCO_vendor_support: vendor-support=0
[  113.217775] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[  113.217892] iTCO_wdt: Found a 6300ESB TCO device (Version=1, TCOBASE=0x0860)
[  113.217935] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  113.277704] EDAC i82875p: i82875p init one
[  113.278022] EDAC MC0: Giving out device to 'i82875p_edac' 'i82875p': DEV 0000:00:00.0
[  113.278056] EDAC PCI0: Giving out device to module 'i82875p_edac' controller 'EDAC PCI controller': DEV '0000:00:00.0' (POLLED)
[  113.357512] Intel 82802 RNG detected
[  113.387561] input: Power Button (FF) as /devices/virtual/input/input3
[  113.427326] ACPI: Power Button (FF) [PWRF]
[  113.427448] input: Power Button (CM) as /devices/virtual/input/input4
[  113.432863] Linux agpgart interface v0.102
[  113.467230] ACPI: Power Button (CM) [PWRB]
[  113.467337] input: Sleep Button (CM) as /devices/virtual/input/input5
[  113.507161] ACPI: Sleep Button (CM) [SLPB]
[  114.555330] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[  114.705002] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  116.112452] NET: Registered protocol family 17
[  119.202503] loop: module loaded
[  119.252184] lp: driver loaded but no devices found
[  119.546177] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[  119.865299] EXT3 FS on sda1, internal journal
[  120.685130] NET: Registered protocol family 10
[  120.685453] lo: Disabled Privacy Extensions
[  121.717325] ip_tables: (C) 2000-2006 Netfilter Core Team

```
There might be something here in the syslog, at the end.  Those message are still continuing to be generated, 30 minutes after the reboot, every 10 seconds:
```

[devvm1: ~]$ tail -n 50 /var/log/syslog
Mar 19 14:05:09 devvm1 kernel: [  113.467230] ACPI: Power Button (CM) [PWRB]
Mar 19 14:05:09 devvm1 kernel: [  113.467337] input: Sleep Button (CM) as /devices/virtual/input/input5
Mar 19 14:05:09 devvm1 kernel: [  113.507161] ACPI: Sleep Button (CM) [SLPB]
Mar 19 14:05:09 devvm1 kernel: [  114.555330] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
Mar 19 14:05:09 devvm1 kernel: [  114.705002] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Mar 19 14:05:09 devvm1 kernel: [  116.112452] NET: Registered protocol family 17
Mar 19 14:05:09 devvm1 kernel: [  119.202503] loop: module loaded
Mar 19 14:05:09 devvm1 kernel: [  119.252184] lp: driver loaded but no devices found
Mar 19 14:05:09 devvm1 kernel: [  119.546177] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
Mar 19 14:05:09 devvm1 kernel: [  119.865299] EXT3 FS on sda1, internal journal
Mar 19 14:05:09 devvm1 kernel: [  120.685130] NET: Registered protocol family 10
Mar 19 14:05:09 devvm1 kernel: [  120.685453] lo: Disabled Privacy Extensions
Mar 19 14:05:09 devvm1 kernel: [  121.717325] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 19 14:05:10 devvm1 postfix/master[4372]: daemon started -- version 2.5.1, configuration /etc/postfix
Mar 19 14:05:10 devvm1 /usr/sbin/cron[4432]: (CRON) INFO (pidfile fd = 3)
Mar 19 14:05:10 devvm1 /usr/sbin/cron[4433]: (CRON) STARTUP (fork ok)
Mar 19 14:05:10 devvm1 /usr/sbin/cron[4433]: (CRON) INFO (Running @reboot jobs)
Mar 19 14:05:16 devvm1 kernel: [  130.874826] eth0: no IPv6 routers present
Mar 19 14:05:21 devvm1 init: tty1 main process (4455) terminated with status 1
Mar 19 14:05:21 devvm1 init: tty1 main process ended, respawning
Mar 19 14:05:31 devvm1 init: tty1 main process (4456) terminated with status 1
Mar 19 14:05:31 devvm1 init: tty1 main process ended, respawning
Mar 19 14:05:41 devvm1 init: tty1 main process (4459) terminated with status 1
Mar 19 14:05:41 devvm1 init: tty1 main process ended, respawning
Mar 19 14:06:51 devvm1 init: tty1 main process (4505) terminated with status 1
Mar 19 14:06:51 devvm1 init: tty1 main process ended, respawning
Mar 19 14:07:01 devvm1 init: tty1 main process (4506) terminated with status 1
Mar 19 14:07:01 devvm1 init: tty1 main process ended, respawning
Mar 19 14:07:11 devvm1 init: tty1 main process (4507) terminated with status 1
Mar 19 14:07:11 devvm1 init: tty1 main process ended, respawning
Mar 19 14:07:21 devvm1 init: tty1 main process (4508) terminated with status 1
Mar 19 14:07:21 devvm1 init: tty1 main process ended, respawning
Mar 19 14:07:31 devvm1 init: tty1 main process (4509) terminated with status 1
Mar 19 14:07:31 devvm1 init: tty1 main process ended, respawning
Mar 19 14:07:41 devvm1 init: tty1 main process (4510) terminated with status 1
Mar 19 14:07:41 devvm1 init: tty1 main process ended, respawning
Mar 19 14:07:51 devvm1 init: tty1 main process (4511) terminated with status 1
Mar 19 14:07:51 devvm1 init: tty1 main process ended, respawning
Mar 19 14:08:01 devvm1 init: tty1 main process (4512) terminated with status 1
Mar 19 14:08:01 devvm1 init: tty1 main process ended, respawning
Mar 19 14:08:11 devvm1 init: tty1 main process (4513) terminated with status 1
Mar 19 14:08:11 devvm1 init: tty1 main process ended, respawning
Mar 19 14:08:21 devvm1 init: tty1 main process (4514) terminated with status 1
Mar 19 14:08:21 devvm1 init: tty1 main process ended, respawning
Mar 19 14:08:31 devvm1 init: tty1 main process (4515) terminated with status 1
Mar 19 14:08:31 devvm1 init: tty1 main process ended, respawning
Mar 19 14:08:41 devvm1 init: tty1 main process (4516) terminated with status 1
Mar 19 14:08:41 devvm1 init: tty1 main process ended, respawning
Mar 19 14:08:51 devvm1 init: tty1 main process (4517) terminated with status 1
Mar 19 14:08:51 devvm1 init: tty1 main process ended, respawning
Mar 19 14:09:01 devvm1 init: tty1 main process (4518) terminated with status 1
Mar 19 14:09:01 devvm1 init: tty1 main process ended, respawning

```
I'm gonna start looking through these now as well, just wanted to post them first.

Thanks again,
uv

---

### Post by uvdevnull on 2009-03-20
I followed the suggested steps listed below and now the error no longer appears, but the boot process still does not finish.

[http://www.linode.com/forums/viewtopic.php?t=3236%3E](http://www.linode.com/forums/viewtopic.php?t=3236%3E)
[http://blog.o-x-t.com/2008/05/09/ttys-killed-on-ubuntu-hardy-heron-vps/](http://blog.o-x-t.com/2008/05/09/ttys-killed-on-ubuntu-hardy-heron-vps/)
[http://www.unixshell.com/forum/showthread.php?p=8228](http://www.unixshell.com/forum/showthread.php?p=8228)

Also, after some research into bootlogd, apparently Ubuntu disabled this feature in the last few releases.

[https://bugs.launchpad.net/upstart/+bug/98955](https://bugs.launchpad.net/upstart/+bug/98955)

---

### Post by fieroboom on 2009-03-20
Ok, one more time, SSH to the machine, and run these commands:
```
cat /etc/event.d/tty1
```
Do that for each tty in /etc/event.d and copy/paste the output here please.
:D
-Paul

EDIT:
I read those links you posted, but I'm not sure *exactly* what you've tried, so I'm still in investigative mode... ;)

---

### Post by uvdevnull on 2009-03-20
Paul,
Good call!
I compared the tty files with another server that didn't have the patches applied and found a difference in tty1.

The working one was:
```

# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty 38400 tty1

```
While the broken one was:
```
# xvc0 - getty
#
# This service maintains a getty on xvc0 from the point the system is
# started until it is shut down again.

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

#respawn
exec /sbin/getty 38400 xvc0

```
So I changed the broken one to mirror the good and was got the console to come up properly! :D
Of course I don't pretend to understand what I did exactly by making that change, but it solved the stated problem.  I'm still researching how Xen works with the ttys.

I was hoping this would also fix the bigger problem of the Xen kernel not booting, but it didn't :(

Is there a way to "uninstall" updates?  Roll-back of some kind? Apparently, the updates did more work than just changing the way tty1 was initialized.  Maybe I can try re-installing Xen from the repos... But then again, there were other updates that might have hosed it, should have done them one at a time I guess...

---

### Post by fieroboom on 2009-03-20
Sweet, I'm glad I could help!
I've never actually used Xen, but I'm usually pretty good at sniifing out problems and chasing errors, so if you've got any errors on it, or want to explain a little more in-depth, let's have it. If I can't help, I'm sure someone else has used Xen and would be able to.
:D
-Paul

---

### Post by 3Miro on 2009-03-20
Once I installed the NVIDIA driver with the NVIDIA script on my 32-bit Ubuntu. After an update, it stopped working. I had to copy the xorg.conf from a 64-bit installation to fix the problem.

If you do things "as supposed to", i.e. use gui tools and don't edit files manually, updates work fine. The only time I had problem with them was when I was going something weird (i.e. run a beta NVIDIA driver or such).

---

### Post by fieroboom on 2009-03-20
> **3Miro said:**
> Once I installed the NVIDIA driver with the NVIDIA script on my 32-bit Ubuntu. After an update, it stopped working. I had to copy the xorg.conf from a 64-bit installation to fix the problem.

If you do things "as supposed to", i.e. use gui tools and don't edit files manually, updates work fine. The only time I had problem with them was when I was going something weird (i.e. run a beta NVIDIA driver or such).

I disagree. This has nothing to do with who edited what and in what way. It is just simply impossible to forsee, catch, and correct *all* bugs upon a new release or an update. It happens. I hate GUIs, and I manually edit all of my files, and I've never had an update issue. It's just luck of the draw.
:D
-Paul

---

### Post by uvdevnull on 2009-03-20
After some more research and comparing config files and kernel boot-time options, I am now able to boot properly again!

Thanks so much for your assistance Paul!

Btw, the inability to log the console screen at boot time in Ubuntu is ridiculous imho.  The screen flashes by so quickly, in some threads discussing this people were actually using cameras to record the output to analyze in slow motion.

---

### Post by fieroboom on 2009-03-20
> **uvdevnull said:**
> After some more research and comparing config files and kernel boot-time options, I am now able to boot properly again!

Thanks so much for your assistance Paul!

Btw, the inability to log the console screen at boot time in Ubuntu is ridiculous imho.  The screen flashes by so quickly, in some threads discussing this people were actually using cameras to record the output to analyze in slow motion.

Awesome! Glad I could help.
In the words of Freddie Mercury:
"And another one gone, and another one gone
Another one bites the dust
Hey, I'm gonna get you too
Another one bites the dust!"
:D
-Paul

---

