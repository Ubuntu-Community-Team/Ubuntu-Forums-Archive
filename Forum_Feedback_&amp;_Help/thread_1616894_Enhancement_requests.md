---
title: "Enhancement requests"
date: 2010-11-08
forum: Forum Feedback &amp; Help
---

### Post by peyre on 2010-11-08
I have what seems like a silly question.  Where's the best place to make enhancement requests for the next version of Ubuntu?

---

### Post by amauk on 2010-11-08
Depends on what it is, really

If it's something relatively simple (Ie. please package application foo), then you can file a wishlist bug on launchpad

If it's a big-picture idea, you can use [Ubuntu Brainstorm]("http://brainstorm.ubuntu.com/")

Or if it's something you are personally working on, then use the ubuntu-devel mailing list to talk directly with the developers

---

### Post by peyre on 2010-11-08
Hey thanks!  I'd like to request smoother handling of removable media (I often have issues with CDs, for instance).  Would that be in the big-picture category?

---

### Post by amauk on 2010-11-08
Yeah,

I'm assuming you're talking hardware specific quirks?
Like some laptops having the eject button on the keyboard rather than on the CD drive itself, and issues with Linux knowing that that button should eject the drive

I'm not quite sure how useful it'll be to add something like that to brainstorm or launchpad, though

Most things like this are already known, and just waiting for the upstream kernel to map the button to a special, non-standard operation

---

### Post by peyre on 2010-11-08
Actually the issue I'm thinking of is that when I insert a CD, the OS doesn't always mount it.

---

### Post by lisati on 2010-11-08
If you think there's a bug, then [launchpad]("http://launchpad.net/") might be the place to check.

---

### Post by Cheesehead on 2010-11-08
What kind of CD mounting problems?
Can you give an example?

What kind of CD? Audio? Data? Install?
You put the CD in the drive, and what happens? What do you expect to happen?
Does it happen for any other CDs?

---

### Post by peyre on 2010-11-08
That's a very good question.  Trouble is that the problem is kind of intermittent.  For example, I've just inserted a burned CD that my daughter brought back from a birthday party.  Exaile opens up on its own, but shows a playlist of some MP3s from my hard drive I had played in it previously.  And when I click on Places, the disk doesn't show there.  'Far as I can tell, the OS fails to mount it properly.  K3B, meanwhile, shows it as an audio CD with 26 minutes of music on it.

Inconsistent behavior like that.

---

### Post by Cheesehead on 2010-11-09
The behavior you describe is a bug or misconfiguration, and should be reported to the Ubuntu Bug Tracker at launchpad.net only AFTER you have done more research on what the failure really is and how to reproduce it.

For example, the most common CD errors are bad burnings - no OS can retrieve data that simply isn't there (even though it may be referenced in the disk index). Can you really access ALL the data on the CD in one application but not another? Or on a different computer? If your friend burns an identical CD, does it behave identically? Does it happen with other burned CDs? Pressed CDs?

Another route is to look at the mounting. Note the time when you pop in a known good CD, and then open /var/log/syslog to that time. You should see messages in the log of the CD being recognized and mounted. Next, do the same with the Troubled CD - how are the syslog messages different? (feel free to post them here)

In order to report a useful bug -one likely to get fixed-, you need to rule out a bad CD or hardware failure, and provide as much detail as possible on how a triager or developer can reproduce the problem using a CD they have handy in their own system...unless you are going to mail them your CD.

Generally, an idea to 'make this already-written software work better' really boils down to bug reporting. The developer worked hard to make it work right the first time, and perhaps you have uncovered something they missed. Good bug reporting is hard work. (But it's better than lazy or bad bug reporting, which gets nothing fixed at all and wastes everyone's time.)

Brainstorm tends to deal with software-that-hasn't-been-written-yet. Like 'I want to add Parental Control features A, B, C, and D to the Movie Player'.

---

### Post by peyre on 2010-11-10
Uh oh!  Those are some pretty involved steps...I'm not sure if my Linux skillz are up to that.

I don't think it's an issue with the individual CD, since I've had these and other inconsistent behavior with lots of different disks (otherwise I wouldn't have posted).  It happens both with CDs I've burned myself, and ones done on other computers.  And with disks burned on both Windows and Linux.  Now that I think of it, it does seem to happen mostly with burned CDs, and not (or not so much) with professionally made ones.

Hm!  Wait, looking at /var/log/syslog--I can do that.  I'll try that tonight when I get home, with both a CD that behaves and one that doesn't.  I wouldn't mind mailing someone this disk, fwiw--it's a mix disk of Miley Cyrus songs.

Yeah, that makes sense, that this is a bug-fix issue rather than a true enhancement request.  That's some level-headed thinking, Cheesehead.

---

### Post by peyre on 2010-11-11
Interesting!  Goes to show what you find out when you pay specific attention.  It looks like my computer accesses disks fine for a while, then at some point kinda-sorta dismounts a disk on its own, and after that you start to have trouble mounting CDs or DVDs.

Earlier tonight, for instance, I had this DVD of .avi clips that I couldn't watch or copy to my HD.  I'd been able to view them in the past, but tonight when I tried, Parole popped up a message saying "Could not read from resource."  If I tried to copy the files to my HD, Thunar would return "Failed to read data from "/media/cdrom0/BBC The Planets - Part 7 Life.avi" (Input/output error)."

I rebooted for other reasons, and now suddenly I'm able to insert the disk and watch movies off it.  So here are my syslogs.  The first is from when I rebooted and had Xubuntu eject the disk that had been in there.  The second is when I put in the disk of AVIs and it read them fine.  Then I inserted several other disks which all read fine, till one of them kinda-sorta dismounted itself.  Then I put the AVI disk back in, and the third syslog is from after inserting it.

---

### Post by peyre on 2010-11-11
Dang!  It didn't save my attachments!  Ok, I'll just push them in here.

Syslog - No CD
```
Nov 11 20:19:07 peyre rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="837" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 11 20:20:14 peyre anacron[953]: Job `cron.daily' terminated (mailing output)
Nov 11 20:20:14 peyre postfix/pickup[1501]: B1C251006D0: uid=0 from=<root>
Nov 11 20:20:14 peyre postfix/cleanup[2668]: B1C251006D0: message-id=<20101112042014.B1C251006D0@peyre>
Nov 11 20:20:14 peyre postfix/qmgr[1502]: B1C251006D0: from=<root@peyre>, size=1405, nrcpt=1 (queue active)
Nov 11 20:20:14 peyre postfix/local[2670]: B1C251006D0: to=<root@peyre>, orig_to=<root>, relay=local, delay=0.24, delays=0.12/0.06/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Nov 11 20:20:14 peyre postfix/qmgr[1502]: B1C251006D0: removed
Nov 11 20:22:08 peyre pulseaudio[2022]: ratelimit.c: 2529 events suppressed
Nov 11 20:22:09 peyre AptDaemon: INFO: Quiting due to inactivity
Nov 11 20:22:09 peyre AptDaemon: INFO: Shutdown was requested
Nov 11 20:22:13 peyre pulseaudio[2022]: ratelimit.c: 2866 events suppressed
Nov 11 20:22:18 peyre pulseaudio[2022]: ratelimit.c: 2492 events suppressed
Nov 11 20:22:23 peyre pulseaudio[2022]: ratelimit.c: 2896 events suppressed
Nov 11 20:22:28 peyre pulseaudio[2022]: ratelimit.c: 2466 events suppressed
Nov 11 20:22:33 peyre pulseaudio[2022]: ratelimit.c: 2935 events suppressed
Nov 11 20:22:38 peyre pulseaudio[2022]: ratelimit.c: 2461 events suppressed
Nov 11 20:23:26 peyre pulseaudio[2022]: ratelimit.c: 1698 events suppressed
Nov 11 20:23:31 peyre pulseaudio[2022]: ratelimit.c: 1792 events suppressed
Nov 11 20:23:36 peyre pulseaudio[2022]: ratelimit.c: 1669 events suppressed
Nov 11 20:23:41 peyre pulseaudio[2022]: ratelimit.c: 1101 events suppressed
Nov 11 20:23:46 peyre pulseaudio[2022]: ratelimit.c: 1616 events suppressed
Nov 11 20:23:51 peyre pulseaudio[2022]: ratelimit.c: 1100 events suppressed
Nov 11 20:24:05 peyre anacron[953]: Job `cron.weekly' started
Nov 11 20:24:05 peyre anacron[3791]: Updated timestamp for job `cron.weekly' to 2010-11-11
Nov 11 20:24:14 peyre anacron[953]: Job `cron.weekly' terminated (mailing output)
Nov 11 20:24:14 peyre anacron[953]: Normal exit (2 jobs run)
Nov 11 20:24:14 peyre postfix/pickup[1501]: 922841006D1: uid=0 from=<root>
Nov 11 20:24:14 peyre postfix/cleanup[3810]: 922841006D1: message-id=<20101112042414.922841006D1@peyre>
Nov 11 20:24:14 peyre postfix/qmgr[1502]: 922841006D1: from=<root@peyre>, size=664, nrcpt=1 (queue active)
Nov 11 20:24:14 peyre postfix/local[3812]: 922841006D1: to=<root@peyre>, orig_to=<root>, relay=local, delay=0.18, delays=0.12/0.01/0/0.05, dsn=2.0.0, status=sent (delivered to mailbox)
Nov 11 20:24:14 peyre postfix/qmgr[1502]: 922841006D1: removed
Nov 11 20:24:38 peyre pulseaudio[2022]: ratelimit.c: 1058 events suppressed
Nov 11 20:24:38 peyre pulseaudio[2022]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Nov 11 20:24:38 peyre pulseaudio[2022]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Nov 11 20:24:38 peyre pulseaudio[2022]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Nov 11 20:24:45 peyre pulseaudio[2022]: ratelimit.c: 46 events suppressed
Nov 11 20:24:50 peyre pulseaudio[2022]: ratelimit.c: 58 events suppressed
Nov 11 20:24:57 peyre pulseaudio[2022]: ratelimit.c: 15 events suppressed
Nov 11 20:25:02 peyre pulseaudio[2022]: ratelimit.c: 52 events suppressed
Nov 11 20:27:48 peyre pulseaudio[2022]: ratelimit.c: 12 events suppressed
```

Syslog - Reads AVI disk fine
```
Nov 11 20:19:07 peyre rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="837" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 11 20:20:14 peyre anacron[953]: Job `cron.daily' terminated (mailing output)
Nov 11 20:20:14 peyre postfix/pickup[1501]: B1C251006D0: uid=0 from=<root>
Nov 11 20:20:14 peyre postfix/cleanup[2668]: B1C251006D0: message-id=<20101112042014.B1C251006D0@peyre>
Nov 11 20:20:14 peyre postfix/qmgr[1502]: B1C251006D0: from=<root@peyre>, size=1405, nrcpt=1 (queue active)
Nov 11 20:20:14 peyre postfix/local[2670]: B1C251006D0: to=<root@peyre>, orig_to=<root>, relay=local, delay=0.24, delays=0.12/0.06/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Nov 11 20:20:14 peyre postfix/qmgr[1502]: B1C251006D0: removed
Nov 11 20:22:08 peyre pulseaudio[2022]: ratelimit.c: 2529 events suppressed
Nov 11 20:22:09 peyre AptDaemon: INFO: Quiting due to inactivity
Nov 11 20:22:09 peyre AptDaemon: INFO: Shutdown was requested
Nov 11 20:22:13 peyre pulseaudio[2022]: ratelimit.c: 2866 events suppressed
Nov 11 20:22:18 peyre pulseaudio[2022]: ratelimit.c: 2492 events suppressed
Nov 11 20:22:23 peyre pulseaudio[2022]: ratelimit.c: 2896 events suppressed
Nov 11 20:22:28 peyre pulseaudio[2022]: ratelimit.c: 2466 events suppressed
Nov 11 20:22:33 peyre pulseaudio[2022]: ratelimit.c: 2935 events suppressed
Nov 11 20:22:38 peyre pulseaudio[2022]: ratelimit.c: 2461 events suppressed
Nov 11 20:23:26 peyre pulseaudio[2022]: ratelimit.c: 1698 events suppressed
Nov 11 20:23:31 peyre pulseaudio[2022]: ratelimit.c: 1792 events suppressed
Nov 11 20:23:36 peyre pulseaudio[2022]: ratelimit.c: 1669 events suppressed
Nov 11 20:23:41 peyre pulseaudio[2022]: ratelimit.c: 1101 events suppressed
Nov 11 20:23:46 peyre pulseaudio[2022]: ratelimit.c: 1616 events suppressed
Nov 11 20:23:51 peyre pulseaudio[2022]: ratelimit.c: 1100 events suppressed
Nov 11 20:24:05 peyre anacron[953]: Job `cron.weekly' started
Nov 11 20:24:05 peyre anacron[3791]: Updated timestamp for job `cron.weekly' to 2010-11-11
Nov 11 20:24:14 peyre anacron[953]: Job `cron.weekly' terminated (mailing output)
Nov 11 20:24:14 peyre anacron[953]: Normal exit (2 jobs run)
Nov 11 20:24:14 peyre postfix/pickup[1501]: 922841006D1: uid=0 from=<root>
Nov 11 20:24:14 peyre postfix/cleanup[3810]: 922841006D1: message-id=<20101112042414.922841006D1@peyre>
Nov 11 20:24:14 peyre postfix/qmgr[1502]: 922841006D1: from=<root@peyre>, size=664, nrcpt=1 (queue active)
Nov 11 20:24:14 peyre postfix/local[3812]: 922841006D1: to=<root@peyre>, orig_to=<root>, relay=local, delay=0.18, delays=0.12/0.01/0/0.05, dsn=2.0.0, status=sent (delivered to mailbox)
Nov 11 20:24:14 peyre postfix/qmgr[1502]: 922841006D1: removed
Nov 11 20:24:38 peyre pulseaudio[2022]: ratelimit.c: 1058 events suppressed
Nov 11 20:24:38 peyre pulseaudio[2022]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Nov 11 20:24:38 peyre pulseaudio[2022]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Nov 11 20:24:38 peyre pulseaudio[2022]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Nov 11 20:24:45 peyre pulseaudio[2022]: ratelimit.c: 46 events suppressed
Nov 11 20:24:50 peyre pulseaudio[2022]: ratelimit.c: 58 events suppressed
Nov 11 20:24:57 peyre pulseaudio[2022]: ratelimit.c: 15 events suppressed
Nov 11 20:25:02 peyre pulseaudio[2022]: ratelimit.c: 52 events suppressed
Nov 11 20:27:48 peyre pulseaudio[2022]: ratelimit.c: 12 events suppressed
Nov 11 20:31:20 peyre kernel: [ 1047.191252] UDF-fs: No VRS found
Nov 11 20:31:20 peyre kernel: [ 1047.191256] UDF-fs: No partition found (1)
Nov 11 20:31:20 peyre kernel: [ 1047.216110] UDF-fs: No VRS found
Nov 11 20:31:20 peyre kernel: [ 1047.216113] UDF-fs: No partition found (1)
Nov 11 20:31:20 peyre kernel: [ 1047.221193] ISO 9660 Extensions: Microsoft Joliet Level 3
Nov 11 20:31:20 peyre kernel: [ 1047.221201] ISOFS: changing to secondary root
Nov 11 20:31:56 peyre pulseaudio[2022]: ratelimit.c: 727 events suppressed
Nov 11 20:32:24 peyre kernel: [ 1111.849005] UDF-fs: No VRS found
Nov 11 20:32:24 peyre kernel: [ 1111.849010] UDF-fs: No partition found (1)
Nov 11 20:32:24 peyre kernel: [ 1111.879076] UDF-fs: No VRS found
Nov 11 20:32:24 peyre kernel: [ 1111.879079] UDF-fs: No partition found (1)
Nov 11 20:32:25 peyre kernel: [ 1111.888353] ISO 9660 Extensions: Microsoft Joliet Level 3
Nov 11 20:32:25 peyre kernel: [ 1111.888361] ISOFS: changing to secondary root
```

Syslog - Same disk after another sort of dismounted itself
```
Nov 11 20:19:07 peyre rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="837" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 11 20:20:14 peyre anacron[953]: Job `cron.daily' terminated (mailing output)
Nov 11 20:20:14 peyre postfix/pickup[1501]: B1C251006D0: uid=0 from=<root>
Nov 11 20:20:14 peyre postfix/cleanup[2668]: B1C251006D0: message-id=<20101112042014.B1C251006D0@peyre>
Nov 11 20:20:14 peyre postfix/qmgr[1502]: B1C251006D0: from=<root@peyre>, size=1405, nrcpt=1 (queue active)
Nov 11 20:20:14 peyre postfix/local[2670]: B1C251006D0: to=<root@peyre>, orig_to=<root>, relay=local, delay=0.24, delays=0.12/0.06/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Nov 11 20:20:14 peyre postfix/qmgr[1502]: B1C251006D0: removed
Nov 11 20:22:08 peyre pulseaudio[2022]: ratelimit.c: 2529 events suppressed
Nov 11 20:22:09 peyre AptDaemon: INFO: Quiting due to inactivity
Nov 11 20:22:09 peyre AptDaemon: INFO: Shutdown was requested
Nov 11 20:22:13 peyre pulseaudio[2022]: ratelimit.c: 2866 events suppressed
Nov 11 20:22:18 peyre pulseaudio[2022]: ratelimit.c: 2492 events suppressed
Nov 11 20:22:23 peyre pulseaudio[2022]: ratelimit.c: 2896 events suppressed
Nov 11 20:22:28 peyre pulseaudio[2022]: ratelimit.c: 2466 events suppressed
Nov 11 20:22:33 peyre pulseaudio[2022]: ratelimit.c: 2935 events suppressed
Nov 11 20:22:38 peyre pulseaudio[2022]: ratelimit.c: 2461 events suppressed
Nov 11 20:23:26 peyre pulseaudio[2022]: ratelimit.c: 1698 events suppressed
Nov 11 20:23:31 peyre pulseaudio[2022]: ratelimit.c: 1792 events suppressed
Nov 11 20:23:36 peyre pulseaudio[2022]: ratelimit.c: 1669 events suppressed
Nov 11 20:23:41 peyre pulseaudio[2022]: ratelimit.c: 1101 events suppressed
Nov 11 20:23:46 peyre pulseaudio[2022]: ratelimit.c: 1616 events suppressed
Nov 11 20:23:51 peyre pulseaudio[2022]: ratelimit.c: 1100 events suppressed
Nov 11 20:24:05 peyre anacron[953]: Job `cron.weekly' started
Nov 11 20:24:05 peyre anacron[3791]: Updated timestamp for job `cron.weekly' to 2010-11-11
Nov 11 20:24:14 peyre anacron[953]: Job `cron.weekly' terminated (mailing output)
Nov 11 20:24:14 peyre anacron[953]: Normal exit (2 jobs run)
Nov 11 20:24:14 peyre postfix/pickup[1501]: 922841006D1: uid=0 from=<root>
Nov 11 20:24:14 peyre postfix/cleanup[3810]: 922841006D1: message-id=<20101112042414.922841006D1@peyre>
Nov 11 20:24:14 peyre postfix/qmgr[1502]: 922841006D1: from=<root@peyre>, size=664, nrcpt=1 (queue active)
Nov 11 20:24:14 peyre postfix/local[3812]: 922841006D1: to=<root@peyre>, orig_to=<root>, relay=local, delay=0.18, delays=0.12/0.01/0/0.05, dsn=2.0.0, status=sent (delivered to mailbox)
Nov 11 20:24:14 peyre postfix/qmgr[1502]: 922841006D1: removed
Nov 11 20:24:38 peyre pulseaudio[2022]: ratelimit.c: 1058 events suppressed
Nov 11 20:24:38 peyre pulseaudio[2022]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Nov 11 20:24:38 peyre pulseaudio[2022]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Nov 11 20:24:38 peyre pulseaudio[2022]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Nov 11 20:24:45 peyre pulseaudio[2022]: ratelimit.c: 46 events suppressed
Nov 11 20:24:50 peyre pulseaudio[2022]: ratelimit.c: 58 events suppressed
Nov 11 20:24:57 peyre pulseaudio[2022]: ratelimit.c: 15 events suppressed
Nov 11 20:25:02 peyre pulseaudio[2022]: ratelimit.c: 52 events suppressed
Nov 11 20:27:48 peyre pulseaudio[2022]: ratelimit.c: 12 events suppressed
Nov 11 20:31:20 peyre kernel: [ 1047.191252] UDF-fs: No VRS found
Nov 11 20:31:20 peyre kernel: [ 1047.191256] UDF-fs: No partition found (1)
Nov 11 20:31:20 peyre kernel: [ 1047.216110] UDF-fs: No VRS found
Nov 11 20:31:20 peyre kernel: [ 1047.216113] UDF-fs: No partition found (1)
Nov 11 20:31:20 peyre kernel: [ 1047.221193] ISO 9660 Extensions: Microsoft Joliet Level 3
Nov 11 20:31:20 peyre kernel: [ 1047.221201] ISOFS: changing to secondary root
Nov 11 20:31:56 peyre pulseaudio[2022]: ratelimit.c: 727 events suppressed
Nov 11 20:32:24 peyre kernel: [ 1111.849005] UDF-fs: No VRS found
Nov 11 20:32:24 peyre kernel: [ 1111.849010] UDF-fs: No partition found (1)
Nov 11 20:32:24 peyre kernel: [ 1111.879076] UDF-fs: No VRS found
Nov 11 20:32:24 peyre kernel: [ 1111.879079] UDF-fs: No partition found (1)
Nov 11 20:32:25 peyre kernel: [ 1111.888353] ISO 9660 Extensions: Microsoft Joliet Level 3
Nov 11 20:32:25 peyre kernel: [ 1111.888361] ISOFS: changing to secondary root
Nov 11 20:33:49 peyre kernel: [ 1196.223760] UDF-fs: Partition marked readonly; forcing readonly mount
Nov 11 20:33:49 peyre kernel: [ 1196.264788] UDF-fs INFO UDF: Mounting volume 'THE_BEER_HUNTER', timestamp 2009/12/24 00:39 (1e20)
Nov 11 20:34:41 peyre kernel: [ 1248.426115] UDF-fs: No VRS found
Nov 11 20:34:41 peyre kernel: [ 1248.426119] UDF-fs: No partition found (1)
Nov 11 20:34:41 peyre kernel: [ 1248.454785] UDF-fs: No VRS found
Nov 11 20:34:41 peyre kernel: [ 1248.454788] UDF-fs: No partition found (1)
Nov 11 20:34:41 peyre kernel: [ 1248.459793] ISO 9660 Extensions: Microsoft Joliet Level 3
Nov 11 20:34:41 peyre kernel: [ 1248.459801] ISOFS: changing to secondary root
Nov 11 20:37:23 peyre kernel: [ 1410.273936] UDF-fs: No VRS found
Nov 11 20:37:23 peyre kernel: [ 1410.273940] UDF-fs: No partition found (1)
Nov 11 20:37:23 peyre kernel: [ 1410.278536] ISO 9660 Extensions: Microsoft Joliet Level 3
Nov 11 20:37:23 peyre kernel: [ 1410.278544] ISOFS: changing to secondary root
Nov 11 20:37:27 peyre kernel: [ 1414.390478] attempt to access beyond end of device
Nov 11 20:37:27 peyre kernel: [ 1414.390484] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:27 peyre kernel: [ 1414.390487] quiet_error: 12 callbacks suppressed
Nov 11 20:37:27 peyre kernel: [ 1414.390489] Buffer I/O error on device sr0, logical block 1236406
Nov 11 20:37:27 peyre kernel: [ 1414.390493] attempt to access beyond end of device
Nov 11 20:37:27 peyre kernel: [ 1414.390495] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:27 peyre kernel: [ 1414.390496] Buffer I/O error on device sr0, logical block 1236407
Nov 11 20:37:27 peyre kernel: [ 1414.390500] attempt to access beyond end of device
Nov 11 20:37:27 peyre kernel: [ 1414.390502] sr0: rw=0, want=4945636, limit=649280
Nov 11 20:37:27 peyre kernel: [ 1414.390504] Buffer I/O error on device sr0, logical block 1236408
Nov 11 20:37:27 peyre kernel: [ 1414.390506] attempt to access beyond end of device
Nov 11 20:37:27 peyre kernel: [ 1414.390508] sr0: rw=0, want=4945640, limit=649280
Nov 11 20:37:27 peyre kernel: [ 1414.390510] Buffer I/O error on device sr0, logical block 1236409
Nov 11 20:37:27 peyre kernel: [ 1414.390514] attempt to access beyond end of device
Nov 11 20:37:27 peyre kernel: [ 1414.390516] sr0: rw=0, want=4945644, limit=649280
Nov 11 20:37:27 peyre kernel: [ 1414.390518] Buffer I/O error on device sr0, logical block 1236410
Nov 11 20:37:27 peyre kernel: [ 1414.390519] attempt to access beyond end of device
Nov 11 20:37:27 peyre kernel: [ 1414.390521] sr0: rw=0, want=4945648, limit=649280
Nov 11 20:37:27 peyre kernel: [ 1414.390523] Buffer I/O error on device sr0, logical block 1236411
Nov 11 20:37:27 peyre kernel: [ 1414.390526] attempt to access beyond end of device
Nov 11 20:37:27 peyre kernel: [ 1414.390528] sr0: rw=0, want=4945652, limit=649280
Nov 11 20:37:27 peyre kernel: [ 1414.390530] Buffer I/O error on device sr0, logical block 1236412
Nov 11 20:37:27 peyre kernel: [ 1414.390532] attempt to access beyond end of device
Nov 11 20:37:27 peyre kernel: [ 1414.390534] sr0: rw=0, want=4945656, limit=649280
Nov 11 20:37:27 peyre kernel: [ 1414.390535] Buffer I/O error on device sr0, logical block 1236413
Nov 11 20:37:27 peyre kernel: [ 1414.390538] attempt to access beyond end of device
Nov 11 20:37:27 peyre kernel: [ 1414.390540] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:27 peyre kernel: [ 1414.390541] Buffer I/O error on device sr0, logical block 1236406
Nov 11 20:37:27 peyre kernel: [ 1414.390543] attempt to access beyond end of device
Nov 11 20:37:27 peyre kernel: [ 1414.390545] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:27 peyre kernel: [ 1414.390547] Buffer I/O error on device sr0, logical block 1236407
Nov 11 20:37:27 peyre kernel: [ 1414.505988] attempt to access beyond end of device
Nov 11 20:37:27 peyre kernel: [ 1414.505997] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:27 peyre kernel: [ 1414.506002] attempt to access beyond end of device
Nov 11 20:37:27 peyre kernel: [ 1414.506004] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144594] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144601] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144605] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144607] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144708] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144711] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144713] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144715] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144748] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144751] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144753] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144755] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144798] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144800] sr0: rw=0, want=5637396, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144803] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144805] sr0: rw=0, want=5637400, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144837] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144840] sr0: rw=0, want=5637396, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144842] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144844] sr0: rw=0, want=5637400, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144879] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144882] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144883] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144885] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144914] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144916] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144918] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144920] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144954] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144957] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144958] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144960] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144994] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.144996] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.144998] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145000] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145026] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145029] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145030] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145032] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145063] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145066] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145067] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145069] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145102] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145104] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145106] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145108] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145141] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145143] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145145] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145147] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145178] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145181] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145183] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145184] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145215] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145218] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145220] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145221] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145251] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145254] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145256] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145258] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145295] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145297] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145299] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145301] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145332] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145335] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145337] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145339] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145370] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145372] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145374] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145376] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145411] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145414] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145416] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145418] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145443] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145446] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145448] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145449] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145479] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145481] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145483] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145485] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145510] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145513] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145515] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145517] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145542] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145544] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145546] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145548] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145573] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145575] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145577] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145579] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145605] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145607] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145609] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145611] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145636] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145638] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145640] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145642] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145666] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145669] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145670] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145672] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145708] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145710] sr0: rw=0, want=5291516, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145712] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145714] sr0: rw=0, want=5291520, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145740] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145742] sr0: rw=0, want=5291516, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145744] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145746] sr0: rw=0, want=5291520, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145770] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145772] sr0: rw=0, want=5291516, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145774] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145776] sr0: rw=0, want=5291520, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145800] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145802] sr0: rw=0, want=5291516, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145804] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145806] sr0: rw=0, want=5291520, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145830] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145832] sr0: rw=0, want=5291516, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145834] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145836] sr0: rw=0, want=5291520, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145859] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145862] sr0: rw=0, want=5291516, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145864] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145865] sr0: rw=0, want=5291520, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145889] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145892] sr0: rw=0, want=5291516, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145894] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145895] sr0: rw=0, want=5291520, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145919] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145922] sr0: rw=0, want=5291516, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145924] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145926] sr0: rw=0, want=5291520, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145950] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145952] sr0: rw=0, want=5291516, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145954] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145956] sr0: rw=0, want=5291520, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145981] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145983] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.145985] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.145987] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146020] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146022] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146024] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146026] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146055] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146058] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146059] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146061] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146095] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146097] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146099] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146101] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146141] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146143] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146145] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146147] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146177] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146180] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146181] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146183] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146213] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146215] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146217] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146219] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146248] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146250] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146252] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146254] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146283] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146286] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146288] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146289] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146319] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146322] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146324] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146325] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146358] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146361] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146363] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146365] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146395] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146397] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146399] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146401] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146431] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146434] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146436] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146437] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146466] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146469] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146471] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146473] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146501] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146504] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146506] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146508] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146536] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146538] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146540] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146542] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146571] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146574] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146576] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146578] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146607] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146609] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146611] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146613] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146637] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146640] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146642] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146644] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146672] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146674] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146676] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146678] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146707] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146709] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146711] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146713] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146741] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146744] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.146746] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.146747] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.147845] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.147850] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.147853] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.147855] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.147904] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.147906] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.147908] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.147910] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.147941] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.147943] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.147945] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.147947] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.147981] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.147983] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.147985] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.147987] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148016] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148018] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148020] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148022] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148051] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148053] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148055] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148057] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148089] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148091] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148093] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148095] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148124] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148126] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148128] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148130] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148155] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148157] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148159] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148161] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148186] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148188] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148190] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148192] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148216] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148218] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148220] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148222] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148246] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148248] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148250] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148252] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148278] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148280] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148282] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148284] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148309] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148311] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148313] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148315] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148339] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148342] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148344] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148345] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148369] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148372] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148374] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148376] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148406] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148408] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148410] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148412] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148437] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148440] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148442] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148443] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148472] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148475] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.148477] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.148479] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157607] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157614] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157617] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157619] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157680] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157682] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157684] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157686] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157717] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157719] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157721] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157723] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157754] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157757] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157759] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157760] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157787] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157789] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157791] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157793] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157822] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157825] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157827] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157828] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157858] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157861] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157863] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157864] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157894] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157896] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157898] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157900] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157929] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157932] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157934] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157936] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157960] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157963] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157965] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157967] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.157996] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.157998] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158000] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158002] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158031] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158034] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158036] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158038] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158072] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158075] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158077] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158079] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158109] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158111] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158113] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158115] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158145] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158147] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158149] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158151] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158181] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158183] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158185] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158187] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158230] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158232] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158234] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158236] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158266] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158268] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158270] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158272] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158303] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158306] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158308] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158309] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158340] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158342] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158344] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158346] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158377] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158379] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158381] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158383] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158412] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158415] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158417] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158419] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158448] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158451] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158453] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158454] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158483] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158486] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158488] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158490] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158519] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158521] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158523] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158525] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158555] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158557] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158559] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158561] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158590] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158592] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158594] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158596] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158627] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158629] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158631] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158633] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158662] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158664] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158666] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158668] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158697] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158699] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158701] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158703] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158732] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158735] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158737] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158738] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158768] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158770] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158772] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158774] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158798] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158801] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158803] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158805] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158833] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158836] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158837] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158839] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158868] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158871] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158872] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158874] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158903] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158906] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158908] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158909] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158938] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158940] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158942] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158944] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158973] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158976] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.158978] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.158980] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159012] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159015] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159017] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159018] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159043] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159045] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159047] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159049] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159073] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159075] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159077] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159079] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159104] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159106] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159108] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159110] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159134] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159137] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159139] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159140] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159171] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159173] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159175] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159177] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159207] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159210] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159211] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159213] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159243] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159246] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159248] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159249] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159279] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159281] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159283] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159285] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159315] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159317] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159319] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159321] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159351] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159353] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159355] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159357] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159386] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159388] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159390] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159392] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159422] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159424] sr0: rw=0, want=5637396, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159427] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159428] sr0: rw=0, want=5637400, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159466] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159468] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159470] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159472] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159503] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159505] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159507] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159509] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159538] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159541] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159543] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159544] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159573] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159576] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159578] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159580] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159609] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159611] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159613] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159615] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159645] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159647] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159649] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159651] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159681] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159683] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159685] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159687] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159718] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159720] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159722] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159724] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159749] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159751] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159753] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159755] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159785] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159787] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159789] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159791] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159821] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159824] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159826] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159827] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159857] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159860] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159862] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159863] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159894] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159897] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159899] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159901] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159931] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159934] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159936] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159937] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159968] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159970] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.159972] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.159974] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.160004] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.160007] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.160009] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.160010] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.160040] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.160042] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.160044] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.160046] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165177] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165183] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165186] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165188] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165248] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165250] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165252] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165254] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165285] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165287] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165289] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165291] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165323] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165325] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165327] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165329] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165359] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165362] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165364] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165365] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165395] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165397] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165399] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165401] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165430] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165433] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165435] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165436] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165467] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165469] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165471] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165473] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165502] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165505] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165507] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165508] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165538] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165540] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165542] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165544] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165573] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165575] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165577] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165579] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165608] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165611] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165613] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165614] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165644] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165646] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165648] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165650] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165679] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165681] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165683] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165685] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165714] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165716] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.165718] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.165720] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.208822] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.208829] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.208832] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.208834] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.208912] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.208914] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.208916] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.208918] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.208952] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.208955] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.208957] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.208959] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.208997] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.208999] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209001] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209003] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209043] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209045] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209047] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209049] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209081] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209084] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209086] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209087] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209119] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209121] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209123] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209125] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209156] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209159] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209161] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209163] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209194] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209196] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209198] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209200] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209231] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209233] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209235] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209237] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209275] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209277] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209279] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209281] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209313] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209315] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209317] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209319] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209350] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209353] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209355] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209356] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209388] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209391] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209393] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209394] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209426] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209428] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209430] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209432] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209463] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209465] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209467] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209469] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209501] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209503] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209505] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209507] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209538] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209541] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209543] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209545] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209576] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209578] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209580] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209582] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209613] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209615] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209617] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209619] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209650] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209652] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.209654] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.209656] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214468] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214473] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214477] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214479] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214539] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214541] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214543] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214545] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214578] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214580] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214582] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214584] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214618] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214620] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214622] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214624] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214659] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214661] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214663] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214665] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214706] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214708] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214710] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214712] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214742] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214744] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214746] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214748] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214778] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214781] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214783] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214785] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214810] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214813] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214815] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214817] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214842] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214844] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214846] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214848] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214873] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214875] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214877] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214879] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214904] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214906] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214908] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214910] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214934] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214937] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214938] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214940] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214971] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214974] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.214976] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.214977] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215017] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215019] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215021] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215023] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215049] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215052] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215054] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215055] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215085] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215088] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215090] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215092] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215117] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215119] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215121] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215123] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215156] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215158] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215160] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215162] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215202] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215205] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215207] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215209] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215241] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215243] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215245] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215247] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215278] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215281] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215283] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215284] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215316] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215318] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215320] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215322] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215353] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215356] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215358] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215360] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215391] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215394] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215396] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215397] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215429] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215431] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215434] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215435] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215467] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215469] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215471] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215473] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215504] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215507] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215509] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215511] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215542] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215545] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215547] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215549] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215580] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215583] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215585] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215587] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215624] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215626] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215628] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215630] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215661] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215664] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215665] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215667] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215701] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215704] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215706] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215707] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215745] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215747] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215749] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215751] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215783] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215786] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215788] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215789] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215821] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215823] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215825] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215827] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215858] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215861] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215863] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215864] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215902] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215904] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215906] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215908] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215940] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215942] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215944] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215946] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215982] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215984] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.215986] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.215988] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216040] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216043] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216045] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216048] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216080] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216083] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216086] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216088] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216120] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216123] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216125] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216128] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216160] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216163] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216166] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216168] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216201] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216204] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216206] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216209] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216241] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216243] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216245] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216247] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216278] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216280] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216282] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216284] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216315] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216318] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216320] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216321] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216353] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216355] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216357] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216359] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216390] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216392] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216394] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216396] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216427] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216429] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216431] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216433] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216464] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216467] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216468] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216470] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216502] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216504] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216506] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216508] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216539] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216542] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:37:28 peyre kernel: [ 1415.216544] attempt to access beyond end of device
Nov 11 20:37:28 peyre kernel: [ 1415.216547] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:38:52 peyre kernel: [ 1498.923669] attempt to access beyond end of device
Nov 11 20:38:52 peyre kernel: [ 1498.923676] sr0: rw=0, want=4945628, limit=649280
Nov 11 20:38:52 peyre kernel: [ 1498.923679] quiet_error: 474 callbacks suppressed
Nov 11 20:38:52 peyre kernel: [ 1498.923681] Buffer I/O error on device sr0, logical block 1236406
Nov 11 20:38:52 peyre kernel: [ 1498.923685] attempt to access beyond end of device
Nov 11 20:38:52 peyre kernel: [ 1498.923687] sr0: rw=0, want=4945632, limit=649280
Nov 11 20:38:52 peyre kernel: [ 1498.923689] Buffer I/O error on device sr0, logical block 1236407
```

---

