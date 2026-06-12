---
title: "can't run mondo rescue on ubuntu?"
date: 2008-12-02
forum: Desktop Environments
---

### Post by djvic87 on 2008-12-02
I downloaded mondo through synaptec manager on ubuntu and restarted the computer and I don't see where it got installed. Can someone tell me how can I run mondo rescue? Do I have to use the terminal? Or where is the installed program located?

Please help, i will appreciate any response, thanks.

---

### Post by pasha07 on 2009-02-25
I have the same problem.. can someone help?

---

### Post by mässgård on 2009-04-06
Graphical interface:
```
sudo mondoarchive
```

If you want to skip the interface check out:
```
man mondoarchive
```

---

### Post by brianpatrick on 2009-04-18
Hi,
I also loaded mondo via Synaptec. It hangs after a few seconds:
brianp@trex:~$ sudo mondoarchive 
Initializing...
See /var/log/mondoarchive.log for details of backup run.
Checking sanity of your Linux distribution
WARNING: Module loop not found.
I think you have a Windows 9x partition.
<< hang forever >>

The last error it complains about in the /var/log/mondoarchive.log file is this:
Mindi v2.0.4-r2045
modinfo: could not find module libata
But then it ends with "...ran just fine. :-)"

I looked for libata in Synaptec, but it is not found. 

Here's the log file below. 

Thank you,

    BrianP

============================================
Time started: Sat Apr 18 14:11:48 2009

running: dmesg -n1 > /r5/mondo.tmp.9qs06z/mondo-run-prog-thing.tmp 2> /r5/mondo.tmp.9qs06z/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran just fine. :-)
Mondo Archive v2.2.7-r2045 --- [http://www.mondorescue.org](http://www.mondorescue.org)
running x86_64 binaries
running on x86_64 architecture
-----------------------------------------------------------
NB: Mondo logs almost everything, so don't panic if you see
some error messages.  Please read them carefully before you
decide to break out in a cold sweat.    Despite (or perhaps
because of) the wealth of messages. some users are inclined
to stop reading this log. If Mondo stopped for some reason,
chances are it's detailed here.  More than likely there's a
message at the very end of this log that will tell you what
is wrong. Please read it!                          -Devteam
-----------------------------------------------------------
Zero...
[Main] mondoarchive.c->welcome_to_mondoarchive#116: One...
	[Main] mondoarchive.c->welcome_to_mondoarchive#117: Two...
		[Main] mondoarchive.c->welcome_to_mondoarchive#118: Three...
			[Main] mondoarchive.c->welcome_to_mondoarchive#119: Four...
	[Main] mondoarchive.c->distro_specific_kludges_at_start_of_mondoarchive#136: Unmounting old ramdisks if necessary
running: mount | grep cdrom | grep super > /r5/mondo.tmp.9qs06z/mondo-run-prog-thing.tmp 2> /r5/mondo.tmp.9qs06z/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran with res=256
running: mount | grep floppy | grep super > /r5/mondo.tmp.9qs06z/mondo-run-prog-thing.tmp 2> /r5/mondo.tmp.9qs06z/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran with res=256
[Main] libmondo-tools.c->mount_boot_if_necessary#1252: Started sub
			[Main] libmondo-tools.c->mount_boot_if_necessary#1253: About to set g_boot_mountpt[0] to '\0'
			[Main] libmondo-tools.c->mount_boot_if_necessary#1255: Done. Great. Seeting command to something
			[Main] libmondo-tools.c->mount_boot_if_necessary#1258: Cool. Command = 'grep -v ":" /etc/fstab | grep -vE '^#.*$' | grep -E "[ 	]/boot[ 	]" | tr -s ' ' '	' | cut -f1 | head -n1'
			[Main] libmondo-tools.c->mount_boot_if_necessary#1260: tmp = ''
[Main] libmondo-tools.c->mount_boot_if_necessary#1298: Ended sub
[Main] libmondo-tools.c->get_kernel_version#262: g_kernel_version = 2.628000
running: rm -Rf /var/cache/mondo/changed.files* > /r5/mondo.tmp.9qs06z/mondo-run-prog-thing.tmp 2> /r5/mondo.tmp.9qs06z/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran just fine. :-)
Checking sanity of your Linux distribution
running: grep ramdisk /proc/devices > /r5/mondo.tmp.9qs06z/mondo-run-prog-thing.tmp 2> /r5/mondo.tmp.9qs06z/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
1 ramdisk
--------------------------------end of output------------------------------
...ran just fine. :-)
running: mount | grep -Ew 'vfat|fat|dos' | grep -vE "/dev/fd|nexdisk" > /r5/mondo.tmp.9qs06z/mondo-run-prog-thing.tmp 2> /r5/mondo.tmp.9qs06z/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
/dev/sde1 on /media/2GB_THUMB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
--------------------------------end of output------------------------------
...ran just fine. :-)
I think you have a Windows 9x partition.
			[Main] libmondo-files.c->find_home_of_exe#434: find_home_of_exe () --- Found cmp at /usr/bin/cmp
running: mindi -V > /r5/mondo.tmp.9qs06z/mondo-run-prog-thing.tmp 2> /r5/mondo.tmp.9qs06z/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
Mindi v2.0.4-r2045
modinfo: could not find module libata
--------------------------------end of output------------------------------
...ran just fine. :-)

---

### Post by irfank on 2010-01-01
I had the same problem, running 9.10 64 bit using the version of Mondo from the repositories. One work around is to completely uninstall Mondo and then go to [ftp://ftp.mondorescue.org/ubuntu/9.10/](ftp://ftp.mondorescue.org/ubuntu/9.10/) to download mondo_2.2.9.1-1_amd64.deb. When you try to install it, you'll get a warning saying that a newer version exists in the repositories. Ignore it and install anyway. 

Problem solved.

---

### Post by irfank on 2010-01-02
I'm afraid I spoke too soon. It wasn't repeatable, and I can't use the archives I created to restore.

Right now, I'm thinking I may just install an earlier version of Ubuntu on a separate partition for the sole purpose of making Mondo backups.

I've also been wondering if it would be possible to put together a very light linux distribution that could run from a USB and whose sole function would be to make Mondo backups. Perhaps Damn Small Linux could be configured for that purpose?

This would help people who have kernels and/or distributions that create problems for Mondo/Mindi but who don't want to recompile or get their hands dirty.

Just an idea.

---

### Post by jamesr on 2010-01-06
That would be an interesting idea but I would suggest that you look at the mondo rescue site, to see if Bruno has done the appropriate build.

I have been using Ubuntu and Mondo for a while. Until recently I trusted it to generate good copies, until a recent update from Ubuntu or so I believe, that was the case. I used to be able to be able to use the CDRW drive but now I cannot verify nor use multiple disks reliably. Verify does not work nor compare, boy was I annoyed. After much experimentation, I have found that if I archive to a USB external drive all seems to work. I will burn to CDRWs if necessary. I am currently in the process of still checking it through, but I would suggest try to archive to an external USB HD drive. 

PS I am currently running 8.04 on a test bed but it was an update that did the damage.

Also look at the FAQs on the mondorescue.org site because there is a reference to changing the update references for Ubuntu, because it is all too easy to have a working system and the Update manager updates it to an older version !!

---

### Post by dartdog on 2010-04-21
FWIW I have a writable dvd mounted and recognized by Lucid..

Help appreciated!!

Downloaded Mondo via synaptic ran sudo mondoarchive
Got Initializing...
Execution run ended; result=-1
type less /var/log/mondoarchive.log to see the output log
That gives me...
TH=9674] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sda

No, Schlomo, that doesn't mean /dev/sda is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=9674] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramdisk? result = 0
[TH=9674] libmondo-tools.c->setup_tmpdir#842: Failed to create global tmp directory /6%/mondo.tmp.xPqfx2 for Mondo.
[TH=9674] libmondo-files.c->register_pid#815: Unregistering PID
[TH=9674] libmondo-files.c->register_pid#817: Error unregistering PID
running: umount /mnt/cdrom > /mondo-run-prog-thing.tmp 2> /mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not found
--------------------------------end of output------------------------------
...ran with res=256
[TH=9732] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sda

No, Schlomo, that doesn't mean /dev/sda is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=9732] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramd/var/log/mondoarchive.log

---

### Post by mistypotato on 2010-04-30
> **irfank said:**
> I had the same problem, running 9.10 64 bit using the version of Mondo from the repositories. One work around is to completely uninstall Mondo and then go to [ftp://ftp.mondorescue.org/ubuntu/9.10/](ftp://ftp.mondorescue.org/ubuntu/9.10/) to download mondo_2.2.9.1-1_amd64.deb. When you try to install it, you'll get a warning saying that a newer version exists in the repositories. Ignore it and install anyway. 

Problem solved.\

Worked.  Thanks :KS (except I downloaded the i386 version.)

---

