---
title: "'dpkg -i' says dependancy is not installed, yet 'dpkg -s' says it is."
date: 2016-12-20
forum: Fedora/RedHat and derivatives
---

### Post by ABC1235 on 2016-12-20
Bear with me here:

In-house, we've rolled several Debian packages.  We've been doing so successfully for years, spanning several Debian releases, but now, Something is Wrong.

We've rolled five packages, each with a set of dependencies.  When we install them in order, the last one won't install successfully.

That fails, saying a dependency is unmet:

    # dpkg -i badge-reader_1.0-53479.20430_all.deb
    (Reading database ... 68089 files and directories currently installed.)
    Preparing to unpack badge-reader_1.0-53479.20430_all.deb ...
    Unpacking badge-reader (1.0-53479.20430) over (1.0-53479.20430) ...
    dpkg: dependency problems prevent configuration of badge-reader:
     badge-reader depends on rfidreader.

    dpkg: error processing package badge-reader (--install):
     dependency problems - leaving unconfigured
    Errors were encountered while processing:
     badge-reader

However, dpkg otherwise asserts that package is indeed installed:
 
    # dpkg -s rfidreader
    Package: rfidreader
    Status: install ok installed
    Priority: optional
    Section: base
    Installed-Size: 96
    Maintainer: [EMAIL="person@example.com"]person@example.com[/EMAIL]
    Architecture: i386
    Source: rfidreader (1.0-0)
    Version: 1.0-53479.20430
    Depends: pcproxapi
    Conffiles:
     /etc/rfidreader/rfidreader.conf d0abd6e1f681e084d0a70548fcefce12
    Description: Our stuff; does things.

There is oddness in our environment:

This is a rebranding of 'trusty', done for an HP thin client.  I have approached them and they swear they did not alter any OS utilities:

    [ftp://ftp.hp.com/pub/tcdebian/OSImages/T7X61007.txt](ftp://ftp.hp.com/pub/tcdebian/OSImages/T7X61007.txt)
    
Our Debian packages are made in a CentOS environment, using a port of the dpkg utilities:

    $ rpm -qa | grep dpkg
    dpkg-devel-1.16.16-5.el6.x86_64
    dpkg-perl-1.16.16-5.el6.noarch
    dpkg-1.16.16-5.el6.x86_64
    dpkg-dev-1.16.16-5.el6.noarch

I don't want to play whack-a-mole trying to upgrade random parts without guidance.

I've attached three files:

log.txt is the output of several commands in our environment, including the installation of two two Debian packages with some debug flags.

rfidreader.strace.txt.zip is the strace of the successful installation of the 'rfidreader' package.

badge-reader.strace.txt.zip is the strace of the unsuccessful installation of the 'badge-reader' package.

If there are any specifics someone would like me to provide, please let me know.

---

### Post by howefield on 2016-12-20
Moved to the "*Fedora/RedHat and derivatives*" forum.

---

