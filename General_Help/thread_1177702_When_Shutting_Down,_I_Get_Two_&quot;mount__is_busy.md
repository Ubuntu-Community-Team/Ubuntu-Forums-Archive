---
title: "When Shutting Down, I Get Two &quot;mount: / is busy&quot; Messages"
date: 2009-06-03
forum: General Help
---

### Post by BryanFRitt on 2009-06-03
During Shutdown I get two "mount: / is busy" messages.
I'm trying to install [IFS]("http://www.fs-driver.org/index.html")([http://www.fs-driver.org](http://www.fs-driver.org)) in Windows Vista to access my Linux partitions, but it's not letting me access them, I suspect it may be due to this error during shutdown "mount: / is busy", which I get two of during shutdown, right before the computer powers off (or reboots). I tried [mountdiag.exe]("http://www.fs-driver.org/download/mountdiag.exe")([http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html)) which gives me something like:
>     * needs_recovery *
Here we have an Ext3 file system which has transactions left in its journal. A
pure Ext2 driver must not access such a volume which is in that state (to
prevent data loss!).
You may solve it by mounting it on Linux (which has a kernel with Ext3
support). Be sure that you cleanly dismount it, before you shutdown Linux.
After that the Ext2 IFS software should be able to access the volume.
   The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not
mount it because there is at least one incompat feature flag set. The Ext2
IFS software does not implement:
    The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not
mount it because the file system has a revision, the Ext2 IFS software does not
implement:
major revision: 0x%lX
minor revision: 0x%hX
copied from the mountdiag.exe file itself, instead of the cmd output.

I've tried *sudo touch /forcefsck* and *sudo shutdown now -r* which reboots and runs the disk scanning utility. Even after that scan, IFS still isn't mounting the partition. I suspect it's related to the two "mount: / is busy" error messages during shutdown I get.

How do I find out what is causing this message?, and what can I do to fix it? Will this fix it so I can access the partiton from [IFS]("http://www.fs-driver.org/index.html")? If not, what else can I do so that I can access the partition using [IFS]("http://www.fs-driver.org/index.html")?

p.s. 
I'm using [KUbuntu]("http://www.kubuntu.org/") 8.0.4.2, I might upgrade to a latter version later though.

---

### Post by BryanFRitt on 2009-06-06
How can I find out what is preventing the harddrive from being unmounted?

---

### Post by BryanFRitt on 2009-06-10
Maybe I'm over my head, but here's what I figured out / done so far

I made an executable file '**S57WhatIsLeft**' in [FONT="Courier New"]/etc/rc0.d/[/FONT]
I think I read somewhere that if I put this in [FONT="Courier New"]/etc/rc6.d/[/FONT] this will run during reboot too, but I didn't try it out.
The Number after the '**S**' represents the execution order position.
```

#! /bin/sh
#BryanFRitt created this to see why I two 'mount: / busy' errors during shutdown
#
#http://www.unix.com/unix-advanced-expert-users/50547-stdout-redirect-file-when-fuser-command-used.html
#http://www.unix.com/302161249-post5.html
# 2>>file.log - this redirects STD ERR
# 1>>file.log - this redirects STD OUT
/bin/fuser -v -m -u /
#Note: I put it in a different directory than posted here.
/bin/fuser -v -m -u / 2> /S57WhatIsLeftOutput.txt 1> /dev/null

```
and added this to the end of '**S60umountroot**' in [FONT="Courier New"]/etc/rc0.d/[/FONT]
```

#java/SchoolClassName/src/
#Without the part the terminal would just close without giving enough time to read it.
#http://content.hccfl.edu/pollock/AUnix1/fancyio.htm
#try Shift+PageUp AND Shift+PageDown to see more of the screen
Pause()
{
    key=""
    echo "\n\n\nPress any key to continue...\n\n"
    stty -icanon
    key=`dd count=1 2>/dev/null`
    stty icanon
}

Pause

```

Right before the '**Pause**' output of '**S60umountroot**' was my '**S57WhatISLeft**' output followed by the two '**mount: / busy**' messages that I have been getting.

The output of my '**S57WhatIsLeftOutput.txt**' file:
[FONT="Courier New"]
                     USER        PID ACCESS COMMAND
/:                   root      .rce. (root)init
                     root      .rc.. (root)kthreadd
                     root      .rc.. (root)migration/0
                     root      .rc.. (root)ksoftirqd/0
                     root      .rc.. (root)watchdog/0
                     root      .rc.. (root)migration/1
                     root      .rc.. (root)ksoftirqd/1
                     root      .rc.. (root)watchdog/1
                     root      .rc.. (root)events/0
                     root      .rc.. (root)events/1
                     root      .rc.. (root)khelper
                     root      .rc.. (root)kblockd/0
                     root      .rc.. (root)kblockd/1
                     root      .rc.. (root)kacpid
                     root      .rc.. (root)kacpi_notify
                     root      .rc.. (root)kseriod
                     root      .rc.. (root)pdflush
                     root      .rc.. (root)pdflush
                     root      .rc.. (root)kswapd0
                     root      .rc.. (root)aio/0
                     root      .rc.. (root)aio/1
                     root      .rc.. (root)ksuspend_usbd
                     root      .rc.. (root)khubd
                     root      .rc.. (root)khpsbpkt
                     root      .rc.. (root)ata/0
                     root      .rc.. (root)ata/1
                     root      .rc.. (root)ata_aux
                     root      .rc.. (root)scsi_eh_0
                     root      .rc.. (root)scsi_eh_1
                     root      .rc.. (root)scsi_eh_2
                     root      .rc.. (root)knodemgrd_0
                     root      .rc.. (root)scsi_eh_3
                     root      .rc.. (root)scsi_eh_4
                     root      .rc.. (root)scsi_eh_5
                     root      .rc.. (root)kjournald
                     root      .rc.. (root)kpsmoused
                     root      .rc.. (root)ntos_wq
                     root      .rc.. (root)ndis_wq
                     root      .rc.. (root)wrapndis_wq
                     root      .rc.. (root)pccardd
                     root      .rc.. (root)btaddconn
                     root      .rc.. (root)btdelconn
                     root      .rc.. (root)kondemand/0
                     root      .rc.. (root)kondemand/1
                     root      .rc.. (root)krfcommd
                     root      frce. (root)rc
                     root      frce. (root)runsvdir
                     root      Frce. (root)runsv
                     gitlog    Frce. (gitlog)svlogd
                     gitdaemon  .rce. (gitdaemon)git-daemon
                     root      Frce. (root)S57WhatIsLeft
[/FONT]
Now what to do next? Any ideas? See anything that might help? Do I need to modify the code anyway to see something else? etc...?

---

### Post by BryanFRitt on 2009-06-11
Right after I completed my last post, found out about the '[FONT="Courier New"]lsof[/FONT]' command
'**S57WhatIsLeft**' can be done like this:
```

#! /bin/sh
#BryanFRitt created this to see why he got two 'mount: / busy' errors during shutdown
#
#[http://www.unix.com/unix-advanced-expert-users/50547-stdout-redirect-file-when-fuser-command-used.html](http://www.unix.com/unix-advanced-expert-users/50547-stdout-redirect-file-when-fuser-command-used.html)
#[http://www.unix.com/302161249-post5.html](http://www.unix.com/302161249-post5.html)
# 2>>file.log - this redirects STD ERR
# 1>>file.log - this redirects STD OUT
#displays to the screen
lsof
/bin/fuser -v -m -u /
#outputs to file '>' restarts the file '>>' appends to the file
#Note: I saved this to my home directory instead of here.
/bin/fuser -v -m -u / 2> /S57WhatIsLeftOutput.txt 1> /dev/null
lsof >> /S57WhatIsLeftOutput.txt

```

---

### Post by cariboo on 2009-06-11
Have you tried running the mount command in a terminal? In a terminal type:

```
mount
```

you should get an output that looks something like this:

```
mount
/dev/sdb1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sdb2 on /home type ext4 (rw,relatime)
/dev/sda1 on /home/storage type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jimk/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jimk)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=jim)
```

Check to see if there is anything unusual.

---

### Post by BryanFRitt on 2009-06-11
Trying```
mount
```(not when shutting down)I get```
/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-24-generic/volatile type tmpfs (rw)
/dev/sda4 on /Drives/Documents_here type ext3 (rw,relatime)
/dev/sda1 on /Drives/Vista type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /Drives/Fantom type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
AFS on /afs type afs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
```

---

### Post by lensman3 on 2009-06-11
Add to your S60 script the file program /usr/sbin/lsof.  It shows everything that a running program is hooked to including file systems, etc.  The "S" means start and "K" means kill for when it shuts down.   Use a K number that is close to 99, that way most of the system has already been killed.  You might take a look at the file "/etc/init.d/halt".  This file is the one on my system that finally umounts everything. 

I use that windows program to access a Linux ext2 drive.  It works very well.  But it only works for a ext2 file system.  If the partition is ext3, it won't work (which is too bad).

In the halt script you might add three "sync" commands so that everything will be flush to the disk, even if it can't be un-mounted.  Another trick is remount the disk as read-only which is the same as unmounted (almost).

Hope this helps.

---

### Post by BryanFRitt on 2009-06-11
> 
I use that windows program to access a Linux ext2 drive.  It works very well.  But it only works for a ext2 file system.  If the partition is ext3, it won't work (which is too bad).


According to [http://www.fs-driver.org/](http://www.fs-driver.org/) [IFS]("http://www.fs-driver.org/") will work with ext3 partitions
> Linux Ext3 volumes can also be accessed.
I have a non root ext3 partition that it works fine with, it just can't do the root one for some reason. I suspect it's because of the 'mount: / busy' errors during shutdown, but I'm not sure.

> 
Another trick is remount the disk as read-only which is the same as unmounted (almost).
I think that is what it is trying to do, but it isn't working.
> 
In the halt script you might add three "sync" commands so that everything will be flush to the disk, even if it can't be un-mounted.
I'll give it a try, Where exactly would it go?, I guess I'll try at the end of my script and at the beginning of the halt.
I tried the above and IFS still doesn't access the drive, same as before. I can give it a letter, but that's it. Same as before.

---

### Post by BryanFRitt on 2009-06-11
I found a message after the 'mount: / is busy' messages. It pops up right before the power cuts off. 'unable to iterate...' didn't read the rest of the message in time.

The end of my shutdown looks like this:
*stopping early crypto disks
mount: / is busy
mount: / is busy
unable to iterate...(missed this part)...No such file or directory
(then something about halt)
then it powerdowns.

---

### Post by BryanFRitt on 2009-06-11
> Another trick is remount the disk as read-only which is the same as unmounted (almost). 
Looking at the code it seams that is what it is trying to do, when I get the message '[FONT="Courier New"]mount: / is busy[/FONT]'
In '[FONT="Courier New"]/etc/rc0.d/S60umountroot[/FONT]'
```
remount_ro () {
	local MTPT=$1
	[ "$VERBOSE" = no ] || log_action_begin_msg "Mounting $MTPT filesystem read-only"
	MOUNT_FORCE_OPT=
	[ "$(uname -s)" = "GNU/kFreeBSD" ] && MOUNT_FORCE_OPT=-f
	# This:
	#     mount -n -o remount,ro /
	# will act on a bind mount of / if there is one.
	# See #339023 and the comment in checkroot.sh
	mount    $MOUNT_FORCE_OPT -n -o remount,ro -t dummytype dummydev $MTPT 2>/dev/null \
	|| mount $MOUNT_FORCE_OPT -n -o remount,ro              dummydev $MTPT 2>/dev/null \
	|| mount $MOUNT_FORCE_OPT -n -o remount,ro                       $MTPT
	ES=$?
	[ "$VERBOSE" = no ] || log_action_end_msg $ES
}
```
from
man mount
>        -n     Mount without writing in /etc/mtab.  This is necessary for exam&#8208;
              ple when /etc is on a read-only file system.

       -o     Options are specified with a -o flag followed by a  comma  sepa&#8208;
              rated  string of options.  Some of these options are only useful
              when they appear in the /etc/fstab file.  The following  options
              apply  to  any  file system that is being mounted (but not every
              file system actually honors them - e.g., the sync  option  today
              has effect only for ext2, ext3, fat, vfat and ufs):

              remount
                     Attempt to remount an already-mounted file system.   This
                     is  commonly  used  to  change the mount flags for a file
                     system, especially to make a readonly file system  write&#8208;
                     able. It does not change device or mount point.

              ro     Mount the file system read-only.

       -t vfstype

---

### Post by BryanFRitt on 2009-06-11
If I add ```
mount
``` to my '**S57WhatIsLeft**' script that runs right before the '[FONT="Courier New"]mount: / busy[/FONT]' messages, I get
```
/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
```
Is there anything that isn't supposed to be there, there?

---

### Post by BryanFRitt on 2009-06-11
I fixed the 
[FONT="Courier New"]unable to iterate ide devices no such file or directory[/FONT]
error message using
[https://bugs.launchpad.net/ubuntu/+bug/193125](https://bugs.launchpad.net/ubuntu/+bug/193125)
[comment number 22]("https://bugs.launchpad.net/ubuntu/+bug/193125/comments/22")

---

### Post by BryanFRitt on 2009-06-12
I tried mounting the drive from a KUbuntu 8.04.1 DVD, witting a couple of folders to the partition, and then deleting some of them, and then umounting the partition, and shutting down.
IFS will work on the partion after that, even showed the changed make while working on the partion with the live DVD. (I bet it'll work until I start back KUbuntu) I deleted some all the files in /tmp/ that it would let me. It said I needed special permission to delete /tmp/kde-bryan/ksyscoca, /tmp/kde-root/ksyscoca, and /tmp/orbit-... 

The fact this works after being mounted by a live CD, appears to be further proof that my system isn't being shutdown nicely. 

I've posted the outputs of '[FONT="Courier New"]mount[/FONT]', '[FONT="Courier New"]lsof[/FONT]', and '[FONT="Courier New"]/bin/fuser -v -m -u /[/FONT]' during shutdown, in my previous posts. Any other ideas of stuff I can do to try to find out what causes the problems, and how to fix it?

---

### Post by BryanFRitt on 2009-06-14
Looking at the shutdown process output I found:

> init: runsvdir main process killed by KILL signal
init: runsvdir main process ended respawning

Could that have something to do with my harddrive being busy? If so what can I do to fix it? What is this doing? What does init, and runsvdir do?

---

### Post by BryanFRitt on 2009-06-16
Fixed it!

I did a google search for [FONT="Courier New"]runsv runsvdir svlogd[/FONT] and found [http://smarden.sunsite.dk/runit/](http://smarden.sunsite.dk/runit/)

So, I decided to see if I could uninstall ([FONT="Courier New"]runit[/FONT]). I used **adept manage**r and selected **runit** to uninstall. It selected **runit**, and **git-daemon-run**. So I clicked to have it uninstall both of those*. And it worked! the two [FONT="Courier New"]mount: / busy[/FONT] messages when away, and now [IFS]("http://www.fs-driver.org/") will mount the partition. (I had to change the [IFS]("http://www.fs-driver.org/") drive letter(in the control panel) to get it working again, although, I could change it back to the old letter right after) 

Thanks, every body who tried to help.


*it may be that I only need to remove **git-daemon-run** to fix the problem, but I didn't test that out.

---

