---
title: "Is mondo/mindi busted on breezy?"
date: 2005-10-23
forum: Desktop Environments
---

### Post by Mustard on 2005-10-23
Everytime I try running mondo I get an error saying that mindi has not been installed properly, because it can't find its version no..  I've uninstalled and reinstalled from synaptic, but I get the same error.  Anyone got mondo working on Breezy yet?

```
seablue@radagast:~$ sudo -i
Password:
root@radagast:~# mondoarchive -O
Initializing...
See /var/log/mondo-archive.log for details of backup run.
Checking sanity of your Linux distribution
I think you have a Windows 9x partition.
Could not ascertain mindi's version number.
You have not installed Mondo and/or Mindi properly.
Please uninstall and reinstall them both.
Fatal error... Please reinstall Mondo and Mindi.
---FATALERROR--- Please reinstall Mondo and Mindi.
Please try the snapshot (the version with 'cvs' and the date in its filename)to see if that fixes the problem. Please don't bother the mailing list withyour problem UNTIL you've tried the snapshot. The snapshot contains bugfixeswhich might help you. Go to http://www.mondorescue.org/download/download.htmlFor more information.
Log file: /var/log/mondo-archive.log
FYI, I have gzipped the log and saved it to /tmp/MA.log.gz
Mondo has aborted.
Execution run ended; result=254
Type 'less /var/log/mondo-archive.log' to see the output log
root@radagast:~#


```

---

### Post by Mustard on 2005-10-24
Updated with terminal output.  I forgot to umount my vfat usb drive before generating this output, but its the same output whether the usb drive is mounted or not.

```
less /var/log/mondo-archive.log
```

gives me this

```
running: dmesg -n1 > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran just fine. :-)
Mondo Archive v2.04 --- http://www.mondorescue.org
running on i386 architecture
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
[Main] main.c->welcome_to_mondoarchive#173: One...
	[Main] main.c->welcome_to_mondoarchive#174: Two...
		[Main] main.c->welcome_to_mondoarchive#175: Three...
			[Main] main.c->welcome_to_mondoarchive#176: Four...
	[Main] main.c->distro_specific_kludges_at_start_of_mondoarchive#193: Unmounting old ramdisks if necessary
running: umount `mount | grep shm | grep mondo | cut -d' ' -f3` > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
Usage: umount [-hV]
umount -a [-f] [-r] [-n] [-v] [-t vfstypes] [-O opts]
umount [-f] [-r] [-n] [-v] special | node...
--------------------------------end of output------------------------------
...ran with res=512
running: mount | grep cdrom | grep super > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran with res=256
running: mount | grep floppy | grep super > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran with res=256
		[Main] libmondo-tools.c->stop_autofs_if_necessary#1366: No autofs detected.
[Main] libmondo-tools.c->mount_boot_if_necessary#1403: Started sub
			[Main] libmondo-tools.c->mount_boot_if_necessary#1404: About to set g_boot_mountpt[0] to '\0'
			[Main] libmondo-tools.c->mount_boot_if_necessary#1406: Done. Great. Seeting command to something
			[Main] libmondo-tools.c->mount_boot_if_necessary#1408: Cool. Command = 'cat /etc/fstab | grep -v ":" | grep -vx "#.*" | grep -w "/boot" | tr -s ' ' '	' | cut -f1 | head -n1'
			[Main] libmondo-tools.c->mount_boot_if_necessary#1410: tmp = ''
[Main] libmondo-tools.c->mount_boot_if_necessary#1453: Ended sub
[Main] libmondo-tools.c->get_kernel_version#409: g_kernel_version = 2.612000
[Main] libmondo-tools.c->reset_bkpinfo#979: Hi
root is mounted at /dev/hda

No, Schlomo, that doesn't mean /dev/hda is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[Main] libmondo-devices.c->am_I_in_disaster_recovery_mode#352: Is this a ramdisk? result = 0
running: rm -Rf /tmp/changed.files* > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran just fine. :-)
Checking sanity of your Linux distribution
	[Main] libmondo-tools.c->some_basic_system_sanity_checks#1105: Free space on given partition = 57 MB
running: cat /proc/devices | grep ramdisk > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
1 ramdisk
--------------------------------end of output------------------------------
...ran just fine. :-)
running: mount | grep -w vfat | grep -v /dev/fd | grep -v nexdisk > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
/dev/sda1 on /media/usbdisk type vfat (rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)
--------------------------------end of output------------------------------
...ran just fine. :-)
I think you have a Windows 9x partition.
			[Main] libmondo-files.c->find_home_of_exe#423: find_home_of_exe () --- Found ms-sys at /usr/bin/ms-sys
			[Main] libmondo-files.c->find_home_of_exe#423: find_home_of_exe () --- Found cmp at /usr/bin/cmp
	[Main] libmondo-tools.c->some_basic_system_sanity_checks#1198: Directory /etc/modprobe.d found. mindi will use its contents.
running: mindi -V > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
/usr/sbin/mindi: line 2345: syntax error near unexpected token `|'
/usr/sbin/mindi: line 2345: `    while [ "`echo "$newo" | grep "\.\."`" ] ; do'
--------------------------------end of output------------------------------
...ran with res=512
Could not ascertain mindi's version number.
You have not installed Mondo and/or Mindi properly.
Please uninstall and reinstall them both.
[Main] newt-specific.c->fatal_error#376: Fatal error received - 'Please reinstall Mondo and Mindi.'
		[Main] newt-specific.c->fatal_error#397: OK, I think I'm the main PID.
	[Main] newt-specific.c->fatal_error#406: I'm going to do some cleaning up now.
			[Main] newt-specific.c->fatal_error#407: killall mindi 2> /dev/null
running: kill `ps wax | grep "/mondo/do-not" | awk '{print $1;}' | grep -vx "\?"` > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran with res=15
running: kill `ps wax | grep "tmp.mondo" | awk '{print $1;}' | grep -vx "\?"` > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran with res=15
running: kill `ps wax | grep "partimagehack" | awk '{print $1;}' | grep -vx "\?"` > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran with res=15
	[Main] newt-specific.c->fatal_error#416: Waiting for child processes to terminate
	[Main] newt-specific.c->fatal_error#416: Waiting for child processes to terminate
	[Main] newt-specific.c->fatal_error#416: Waiting for child processes to terminate
	[Main] newt-specific.c->fatal_error#416: Waiting for child processes to terminate
	[Main] newt-specific.c->fatal_error#416: Waiting for child processes to terminate
	[Main] newt-specific.c->fatal_error#416: Waiting for child processes to terminate
	[Main] newt-specific.c->fatal_error#416: Waiting for child processes to terminate
	[Main] newt-specific.c->fatal_error#416: Waiting for child processes to terminate
	[Main] newt-specific.c->fatal_error#416: Waiting for child processes to terminate
	[Main] newt-specific.c->fatal_error#416: Waiting for child processes to terminate
Please DON'T contact the mailing list. Try the SNAPSHOTS.
	[Main] libmondo-files.c->register_pid#815: Unregistering PID
	[Main] libmondo-files.c->register_pid#815: Unregistering PID
	[Main] libmondo-files.c->register_pid#816: Error unregistering PID
running: umount /mnt/cdrom > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not mounted
--------------------------------end of output------------------------------
...ran with res=256
running: rm -Rf /mondo.scratch.* /tmp.mondo.* > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran just fine. :-)
running: rm -Rf   > /tmp/mondo-run-prog-thing.tmp 2> /tmp/mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
--------------------------------end of output------------------------------
...ran just fine. :-)
	[Main] libmondo-tools.c->do_libmondo_global_strings_thing#1603: libmondo-tools.c, do_libmondo_global_strings_thing, 1603: Freeing globals
```

I don't know what more I can do to install it properly, other than purging the mondo and mindi installations and then reinstalling through apt-get/synaptic.  I've done this mulitple times now, with the same result.

---

### Post by Mustard on 2005-10-24
*bump*

Just rescuing this off page three......

---

### Post by Mustard on 2005-10-24
*bump*

hmmm..found it on page 5 this time.....

---

### Post by Mustard on 2005-10-24
Confirmed bug it seems.

[https://launchpad.net/distros/ubuntu/+sources/mondo/+bug/3174](https://launchpad.net/distros/ubuntu/+sources/mondo/+bug/3174)

---

### Post by dehuszar on 2005-11-05
Incidentally, I think the problem is with Mindi.

When run alone on a clean breezy install I get this:

```
/usr/sbin/mindi: line 2345: syntax error near unexpected token `|'
/usr/sbin/mindi: line 2345: `    while [ "`echo "$newo" | grep "\.\."`" ] ; do'

```

Without Mindi, MondoRescue will not work.

I will try to build mindi manually to confirm.

Sam

---

### Post by dehuszar on 2005-11-05
Well after searching around and playing about I've discovered the following.

The latest debs (Debian Sid) for Mondo and Mindi are newer than our Ubuntu debs and require (mindi-partimagehack, specifically) a newer version of libstdc++6 than Ubuntu currently provides.  Not wanting to mess with that particular hornet's nest, I went and DLed the Ubuntu Hoary debs for mindi and mondo from:

[http://packages.ubuntu.com/hoary/utils/](http://packages.ubuntu.com/hoary/utils/)

Prior to installation, Breezy needs slang1a-utf8 installed.  Then the Hoary debs will install and Mondo and Mindi will run.  It's not the latest and greatest, nor is it exciting to see the upgrades available notification for items you shouldn't upgrade to, but hey!  It works!!

Hope that helps yall.

Sam

---

### Post by Shaggy on 2005-11-10
THanks for this info, I just installed mondo and came across this problem.  Nice to know I wasn't alone.

---

### Post by Mustard on 2005-11-10
Lately I have been visiting the launchpad site to see what is happening with either mondo or mindi and I can't even find them using the package search anymore. Launchpad seems to think that mondo and mindi don't exist.

---

### Post by Pausanias on 2005-11-12
Here is the page you need to look at

[https://launchpad.net/distros/ubuntu/+source/mindi/+bug/2904](https://launchpad.net/distros/ubuntu/+source/mindi/+bug/2904)

Make the change he suggests to /usr/sbin/mindi and then you're set. There is no need to revert to the hoary version. The libc bug has in fact been fixed; this is a separate bug with a misplaced "`".

---

### Post by redmoon on 2005-11-15
Excellent!

Thanks for the help.

---

### Post by Mustard on 2005-11-15
[QUOTE=Pausanias]Here is the page you need to look at

[https://launchpad.net/distros/ubuntu/+source/mindi/+bug/2904](https://launchpad.net/distros/ubuntu/+source/mindi/+bug/2904)

Make the change he suggests to /usr/sbin/mindi and then you're set. There is no need to revert to the hoary version. The libc bug has in fact been fixed; this is a separate bug with a misplaced "`".[/QUOTE]

Fabulous!  I've been eagerly awaiting this fix. :)

---

### Post by haddog on 2005-12-01
This info was found using this forum. I'm just typing it here so you don't have to look for it. Here is what I did to get Mondo to work. It has to do with Mindi. There is a typo which renders Mindi unusable. You have to edit Line 2269 of /usr/sbin/mindi . I used gedit to edit /usr/sbin/mindi as follows using Gnome Terminal.

haddog@hubuntu:~$ sudo gedit /usr/sbin/mindi

The file will open. There is a missing character  ` on line 2269. Line 2269 should be as follows: 

for fname in `echo "$incoming"` ; do

Once you add the missing  `  character, save the file and close it. Next I started Mondo from a Gnome Terminal using the sudo command like this:

haddog@hubuntu:~$ sudo mondoarchive

Follow the on-screen prompts. Sit back and watch your backup do it's thang!

---

### Post by teomatto on 2006-01-17
i simply manually download the mindi and mondo packages (after removing the apt ones) and reinstall them with dpkg -i from [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fm%2Fmondo%2Fmondo_2.04-3_i386.deb&md5sum=7358c8d36e251b945ad12f27dffdef5c&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fm%2Fmondo%2Fmondo_2.04-3_i386.deb&md5sum=7358c8d36e251b945ad12f27dffdef5c&arch=i386&type=main)

after this action, all seem to work 
hope help

matteo

---

