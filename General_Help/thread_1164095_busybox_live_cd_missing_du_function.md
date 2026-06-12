---
title: "busybox live cd missing du function"
date: 2009-05-19
forum: General Help
---

### Post by dstempfley on 2009-05-19
I'm having problems booting my ubuntu live cd.  The casper log seems has the error:

  /init: line 1: du: not found

When I set -x and trace the execution of casper command I get: 

+ doumount=1
+ [ used = used ]
+ du -ks /mnt/tmp_fs_size
/init: line 1: du: not found
+ cut -f1
+ size=
+ expr + / 20
expr: non-numeric argument
+ size=

This is from the casper-helpers script and being called in the fs_size function.

I did a break to look at why busybox wouldn't find du, since it's supposed to be internal.  

When I type "busybox" at the command prompt in the stopped boot process:

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) multi-call binary
Copyright (C) 1998-2007 Erik Andersen, Rob Landley, Denys Vlasenko
and others. Licensed under GPLv2.
See source distribution for full notice.

Usage: busybox [function] [arguments]...
   or: function [arguments]...

	BusyBox is a multi-call binary that combines many common Unix
	utilities into a single executable.  Most people will create a
	link to busybox for each function they wish to use and BusyBox
	will act like whatever it was invoked as!

Currently defined functions:
	[, [[, ash, awk, basename, cat, chmod, chroot, chvt, clear,
	cmp, cp, cut, deallocvt, dumpkmap, echo, egrep, env, expr,
	false, fbset, fdflush, fgrep, find, grep, hostname, ifconfig,
	ip, kill, ln, loadfont, loadkmap, ls, mkdir, mkfifo, mknod,
	mkswap, mktemp, more, mount, mv, openvt, pidof, printf,
	ps, pwd, readlink, reset, rm, rmdir, sed, setkeycodes,
	sh, sleep, sort, stat, stty, sync, tail, tee, test, touch,
	tr, true, tty, umount, uname, uniq, wget, yes

There is no du listed.

And on my live system I get: 

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) multi-call binary
Copyright (C) 1998-2007 Erik Andersen, Rob Landley, Denys Vlasenko
and others. Licensed under GPLv2.
See source distribution for full notice.

Usage: busybox [function] [arguments]...
   or: function [arguments]...

	BusyBox is a multi-call binary that combines many common Unix
	utilities into a single executable.  Most people will create a
	link to busybox for each function they wish to use and BusyBox
	will act like whatever it was invoked as!

Currently defined functions:
	[, [[, adjtimex, arping, ash, awk, basename,
	brctl, bunzip2, bzcat, bzip2, cal, cat, chgrp,
	chmod, chown, chroot, chvt, clear, cmp, cp,
	cpio, cut, date, dc, dd, deallocvt, df, dirname,
	dmesg, dos2unix, du, dumpkmap, echo, egrep,
	env, expr, false, fgrep, find, fold, free,
	ftpget, ftpput, getopt, grep, gunzip, gzip,
	head, hexdump, hostid, hostname, httpd, id,
	ifconfig, ip, ipcalc, kill, killall, klogd,
	last, length, ln, loadfont, loadkmap, logger,
	logname, logread, losetup, ls, lzmacat, md5sum,
	mdev, mkdir, mkfifo, mknod, mktemp, more, mount,
	mt, mv, nameif, nc, netstat, nslookup, od,
	openvt, patch, pidof, ping, ping6, printf,
	ps, pwd, rdate, readlink, realpath, renice,
	reset, rm, rmdir, route, rpm, rpm2cpio, run-parts,
	sed, setkeycodes, sh, sha1sum, sleep, sort,
	start-stop-daemon, strings, stty, swapoff,
	swapon, sync, sysctl, syslogd, tac, tail, tar,
	tee, telnet, test, tftp, time, top, touch,
	tr, traceroute, true, tty, umount, uname, uncompress,
	uniq, unix2dos, unlzma, unzip, uptime, usleep,
	uudecode, uuencode, vi, watch, watchdog, wc,
	wget, which, who, whoami, xargs, yes, zcat

There it is.

Since the versions are the same, why are there different functions supported.  Also, since this is a stock casper, Are others having this problem?  Any ideas on how should I resolve it?

Thanks,

/Dion

---

### Post by dstempfley on 2009-05-20
I don't have any answers about why, and I presume that I'm not the only person with the issue, but I fixed this.  

Since it's a live cd that I'm remastering, I set up a chrooted environment for my root filesystem and installed ran "apt-get install busybox-static"

Then I edited /usr/sbin/mkinitramfs and changed BUSYBOXDIR from /usr/lib/initramfs-tools/bin to /bin

Still wish I knew why the same version of busybox would have different applets compiled in.

/Dion

---

