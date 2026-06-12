---
title: "Studio XPS 13 hibernate"
date: 2009-02-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ztom on 2009-02-23
Hi,

Using new XPS 13 is fantastic, but there are few issues before I would feel comfortable erasing vista partition completely, one of them is..

I have read many instructions about hibernate, installed hibernate package and so on,

and reached a state where I can nicely hibernate ubuntu with a command
```
sudo s2disk
```

After that I see messages about writing memory image to swap and so on. On restart I get working desktop back. I have not checked specially, but seems like everything I use works normally.

If I click hibernate from shutdown menu on the right upper corner( or power button ), the screen goes blank with blinking cursor upper left corner, *something* is written to hdd (HDD light is on for a while), power gets cut.. but booting up ubuntu behaves like it had a crash: it checks uncleanly unmounted partitions and boots like after shutdown, not resuming from hibernate.

I have gone trough /etc/hibernate/hibernate.conf and (un)commenting
lines in disk.conf (current state: )
```
#TryMethod ususpend-disk.conf
TryMethod sysfs-disk.conf

```

Nothing seems to have effect there.

Does this seem more like general issue with ubuntu or specific to computer?

What really happens when I use the menu? maybe I'm just digging in totally unrelated conf files..

Or where can I modify commands, that get execued when I use the power button menu? seems like "unelegant" solution for me may be just changing the command used there to "s2disk".

Thanks,
Tom

---

### Post by superm1 on 2009-02-24
You shouldn't be installing any 'hibernate' package.  It should just be operating "out of the box" with the pm-hibernate command (or selecting hibernate from the menu).

What's happening when you are trying using those standard methods?

---

### Post by ztom on 2009-02-24
> **superm1 said:**
> 
What's happening when you are trying using those standard methods?

Ok, I uninstalled hibernate package and tried pm-hibernate. It behaves exactly as hibernate command from shutdown menu:
> If I click hibernate from shutdown menu on the right upper corner( or power button ), the screen goes blank with blinking cursor upper left corner, *something* is written to hdd (HDD light is on for a while), power gets cut.. but booting up ubuntu behaves like it had a crash: it checks uncleanly unmounted partitions and boots like after shutdown, not resuming from hibernate.

Hopefully it was obvious enough, but I forgot to mention, that I'm trying this with Ubuntu 8.10 version (with Estonian translations, if this has any effect). Of course compiz and nvidia 177 drivers active.

Now I found also /etc/pm/* config directory, it has default kernel method configured, but I see that it would be trivial to change it to use hibernate package with "uswsusp" option. I know already that this works. What can I check out before "giving up" and using just that?

only log I found is /var/log/pm-suspend.log
```
Initial commandline parameters: 
T veebr 24 15:36:18 EET 2009: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/00clear hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate: success.
/usr/lib/pm-utils/sleep.d/05led hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager hibernate: success.
/usr/lib/pm-utils/sleep.d/48hid2hci hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/50modules hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate: success.
/usr/lib/pm-utils/sleep.d/95led hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate: success.
T veebr 24 15:36:23 EET 2009: performing hibernate

```

Can I force it to be more verbose?

From booting up first indication of any HDD access I see is this(dmesg):
```
[    7.066604] EXT3-fs: INFO: recovery required on readonly filesystem.
[    7.066608] EXT3-fs: write access will be enabled during recovery.
[    9.737612] kjournald starting.  Commit interval 5 seconds
[    9.737655] EXT3-fs: sda2: orphan cleanup on readonly fs
[    9.737659] ext3_orphan_cleanup: deleting unreferenced inode 85298
[    9.737692] ext3_orphan_cleanup: deleting unreferenced inode 139903
[    9.737704] EXT3-fs: sda2: 2 orphan inodes deleted
[    9.737705] EXT3-fs: recovery complete.
[    9.766937] EXT3-fs: mounted filesystem with ordered data mode.

```
Which is clearly not a good sign.
cd /var/log & grep "pm-" * gave only this interesting line( there were uninteresting ones from dpkg.log,pm-suspend.log, auth.log, ... ):

```
syslog.0:Feb 24 01:23:33 computer-name kernel: [16135.446515] Pid: 18423, comm: pm-suspend Tainted: P          2.6.27-11-generic #1
```

Without any other hints I come to conclusion, that for some reason the power gets cut before the hibernation operation is finalized on disk.

---

### Post by superm1 on 2009-02-24
> **ztom said:**
> Ok, I uninstalled hibernate package and tried pm-hibernate. It behaves exactly as hibernate command from shutdown menu:


Hopefully it was obvious enough, but I forgot to mention, that I'm trying this with Ubuntu 8.10 version (with Estonian translations, if this has any effect). Of course compiz and nvidia 177 drivers active.

Now I found also /etc/pm/* config directory, it has default kernel method configured, but I see that it would be trivial to change it to use hibernate package with "uswsusp" option. I know already that this works. What can I check out before "giving up" and using just that?

only log I found is /var/log/pm-suspend.log
```
Initial commandline parameters: 
T veebr 24 15:36:18 EET 2009: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/00clear hibernate: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate: success.
/usr/lib/pm-utils/sleep.d/05led hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager hibernate: success.
/usr/lib/pm-utils/sleep.d/48hid2hci hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/50modules hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate: success.
/usr/lib/pm-utils/sleep.d/95led hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate: success.
T veebr 24 15:36:23 EET 2009: performing hibernate

```Can I force it to be more verbose?

From booting up first indication of any HDD access I see is this(dmesg):
```
[    7.066604] EXT3-fs: INFO: recovery required on readonly filesystem.
[    7.066608] EXT3-fs: write access will be enabled during recovery.
[    9.737612] kjournald starting.  Commit interval 5 seconds
[    9.737655] EXT3-fs: sda2: orphan cleanup on readonly fs
[    9.737659] ext3_orphan_cleanup: deleting unreferenced inode 85298
[    9.737692] ext3_orphan_cleanup: deleting unreferenced inode 139903
[    9.737704] EXT3-fs: sda2: 2 orphan inodes deleted
[    9.737705] EXT3-fs: recovery complete.
[    9.766937] EXT3-fs: mounted filesystem with ordered data mode.

```Which is clearly not a good sign.
cd /var/log & grep "pm-" * gave only this interesting line( there were uninteresting ones from dpkg.log,pm-suspend.log, auth.log, ... ):

```
syslog.0:Feb 24 01:23:33 computer-name kernel: [16135.446515] Pid: 18423, comm: pm-suspend Tainted: P          2.6.27-11-generic #1
```Without any other hints I come to conclusion, that for some reason the power gets cut before the hibernation operation is finalized on disk.

I'm wondering if you might be plagued by one of the disks that is taking a long time to recover from a suspend on Intrepid.  If so, that's solved on Jaunty.  Otherwise, perusing your logs isn't showing anything interesting.

Until you are comfortable testing with Jaunty, perhaps can you just use S3 instead?

---

### Post by ztom on 2009-02-24
My XPS 13 has 250GB SATA drive, but who knows.. luckily local dealer gave 5 year warranty with this very new model, so if the heat will not kill it first, then ..

> **superm1 said:**
> Until you are comfortable testing with Jaunty, perhaps can you just use S3 instead?

I am currently in testing mood anyway, so I'll take a shot at Jaunty, as I see it's "only" 2 months until release.. but then again it says there is some wirdness about nvidia drivers going on.. but I can always do clean 8.10 install again, wasn't that difficult.

Thanks for the advice!
Toomas

---

### Post by ztom on 2009-02-24
Sad news: hibernate behaves same way on Jaunty, so probably it's not my HDD causing the problem.

Somewhat better news is, that Apport caught this and I reported bug #334103, hopefully it will be some use.

Next thing to try: clean Jaunty install! This problem persists after upgrade from 8.10

---

### Post by ztom on 2009-02-24
YAY!

Clean Jaunty install did it! hibernate works!

There are some warnings and "concerns" about some devices being reset, but first impression is, that it works!

It took some time to play around with some packages and synaptic touchpad driver for xorg is not installed by default!!! It was a funny scare, seeing dead mouse on the screen and little excercise in keyboard control, but I got it installed without connecting external mouse ;)

Now only few bells are missing, everything I have tried so far is working.

Nvidia drivers or something else also work obviously better: system monitor for example took constantly 30% of one core previously, now only 1..4% ( those scrolling graphs probably played crazy )

Thanks for the Jaunty tip! I would have not gone this route myself probably, but it was totally worth it in more ways than just fixing hibernate.

Toomas

---

### Post by superm1 on 2009-02-24
I really wonder what was causing these problems then. That's really odd that it "just worked" on 9.04 clean but not upgrade.  Can you close out that bug then?

If the problems come back (hope not :)) then open another one up.

---

