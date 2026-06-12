---
title: "Putting a package on Hold"
date: 2012-03-15
forum: Desktop Environments
---

### Post by metallica1973 on 2012-03-15
I am try to hold back nfs-common from updating:

so I put a package on hold like this

[php]echo "package hold" | sudo dpkg --set-selections

Remove the hold

echo "package install" | sudo dpkg --set-selections
[/php]

[http://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package](http://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package)

but I get this:

[php]dpkg --status nfs-common
Package: nfs-common
Status: hold ok half-configured
Priority: standard
Section: net
Installed-Size: 588
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: nfs-utils
Version: 1:1.2.0-4ubuntu4.2
Config-Version: 1:1.2.0-4ubuntu4.1
Replaces: mount (<< 2.13~), nfs-client, nfs-kernel-server (<< 1:1.0.7-5)
Provides: nfs-client
Depends: portmap (>= 6.0.0-1ubuntu2.1), adduser, ucf, lsb-base (>= 1.3-9ubuntu3), netbase (>= 4.24), initscripts (>= 2.86.ds1-38.1), libc6 (>= 2.4), libcomerr2 (>= 1.01), libevent-1.4-2 (>= 1.4.13-stable), libgssapi-krb5-2 (>= 1.6.dfsg.2), libgssglue1, libk5crypto3 (>= 1.6.dfsg.2), libkrb5-3 (>= 1.6.dfsg.2), libnfsidmap2, librpcsecgss3, libwrap0 (>= 7.6-4~), upstart-job
Conflicts: nfs-client
Conffiles:
/etc/init/statd.conf d5e9dea3d4f694078db7a2da8478dfb0
/etc/init/statd-mounting.conf d9cbcb804d4aa0ce5b69796c79ef1b6e
/etc/init/gssd.conf d49da5ecdc9771e1e8e42caf25bbfa4a
/etc/init/idmapd.conf 401837b3f91489f86545cb8c8277a7c0
Description: NFS support files common to client and server
Use this package on any machine that uses NFS, either as client or
server. Programs included: lockd, statd, showmount, nfsstat, gssd
and idmapd.
.
Upstream: SourceForge project "nfs", CVS module nfs-utils.
Homepage: http://nfs.sourceforge.net/
Original-Maintainer: Anibal Monsalve Salazar <anibal@debian.org>
root@SAINTStick:~# dpkg -l nfs-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name Version Description
+++-==============-==============-============================================
hF nfs-common 1:1.2.0-4ubunt NFS support files common to client and serve [/php]

---

