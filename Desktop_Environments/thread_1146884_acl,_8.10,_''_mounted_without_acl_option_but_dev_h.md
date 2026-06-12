---
title: "acl, 8.10, '/' mounted without acl option but /dev has non-base acl's"
date: 2009-05-03
forum: Desktop Environments
---

### Post by treeflyr on 2009-05-03
Hello All,

I am currently running ubuntu 8.10 64bit desktop on ASUS M3N-HT mb, and have noticed the output from this command:

> sudo getfacl --skip-base --recursive /dev 2>/dev/null|grep file:

# file: dev/audio
# file: dev/mixer
# file: dev/dsp
# file: dev/adsp
# file: dev/sequencer2
# file: dev/sequencer
# file: dev/snd/controlC0
# file: dev/snd/pcmC0D0c
# file: dev/snd/pcmC0D0p
# file: dev/snd/pcmC0D1c
# file: dev/snd/pcmC0D1p
# file: dev/snd/seq
# file: dev/snd/timer
# file: dev/scd0
# file: dev/fuse

But when I look at mount options for root I see the following:

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)

Which tells me that the file-system for '/' is mounted without acl enabled, but I am seeing the above when I look for all non-base acl's in /dev on this file-system.

The reason all this is important to me is that I have a perl backup script (mkbkup.pl) and want to release a version 4.0 of this script soon that plays well with ubuntu.  The development version I have of this script works just fine if I boot up or reboot into recovery mode.

When I do that I am able to make bootable backups of my ubuntu system just fine (This is what mkbkup.pl does).  However I would like to be able to run my mkbkup.pl script after dropping into single user mode from desktop (runlevel 2 on my box).  

What I have noticed though is that the script borks due to permissions problems in copying /dev to the backup partition (with 'cp -a').  

I verified that if I reboot (or cold boot) into recovery mode then getfacl --skip-base returns no non-base acl files, and also my backup script runs cleanly.

However (either in runlevel 2 or dropping to single user from runlevel 2) cp -a /dev /bkup_xxx/dev fails due to permissions problems (on the above entries). And thusly the backup script fails also.

It appears that switching to runlevel 2 causes non-base acl stanzas to be added to certain files in /dev in '/' (root file system) even though I can see that this file-system is mounted without acl enabled.

I don't know if this is a bug or there is something I am missing.

Ideally I would like to be able to run my backup script by dropping into single user mode from my runlevel 2 (desktop situation) as a prelude to powering off the machine for the evening, but for now I can live with rebooting to recovery (single user mode) and running the mkbkup.pl in that situation.

Of course I can perform the mount of the backup partition with acl option and the copy would probably be done cleanly, but then I run the risk of the backup not reflecting what the original looks like when you compare the profiles of both systems in recovery mode. 

Note: I also tried stopping all the services that get started in /etc/rc2.d, after dropping to single user, but none of that turned off these "transient" acls.

Any help or pointers would be appreciated.

I plan to publish mkbkup.ver.4.0 soon after some more testing on my ubuntu box and also my old Suse10.0 box in order to insure mkbkup.pl remains golden in the legacy situation.

Regards,
Newton Hammet

---

### Post by treeflyr on 2009-05-04
Hello Everyone,

I think I have found a way out of my acl conundrum.  I just tested a theory on my box that the /dev directory is built on boot, and so doing a recursive archiving copy ('cp -a') is not necessary. On the backup drive I moved its dev directory to another location and created and empty dev directory in its place.  I was able to boot the backup drive normally and it got populated with all the necessary devices.

For the purposes of my backup script (mkbkup.pl) I can simply perform a mkdir of the /dev directory on the backup drive, as opposed to doing a recursive archive copy of the contents of '/dev'. 

I will also do some reading of documentation I can find on this subject, to see if this nice feature is widespread among different distros (Fedora, Suse, et al, as well as ubuntu, and other Debian-centric builds.)

I will post my conclusions here in this thread.

-treeflyr

---

