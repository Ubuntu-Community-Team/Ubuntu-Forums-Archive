---
title: "Managing services"
date: 2006-06-05
forum: Desktop Environments
---

### Post by lzap on 2006-06-05
Hello, is there some tool for console for managing services? Starting, stopping and adding, removing, disabling, enabling? Just like rc-update in Gentoo or service in Mandriva...

---

### Post by lzap on 2006-06-05
I know there is that "BUM" app, but I found it very complicated and it even do not work (as I expect).

---

### Post by llamakc on 2006-06-05
I'm partial to rcconf:

ken@vulva:~$ apt-cache show rcconf
Package: rcconf
Priority: optional
Section: universe/admin
Installed-Size: 112
Maintainer: Atsushi KAMOSHIDA <kamop@debian.org>
Architecture: all
Version: 1.17
Depends: whiptail | whiptail-provider | dialog, sysv-rc, perl, perl-modules
Conflicts: file-rc
Filename: pool/universe/r/rcconf/rcconf_1.17_all.deb
Size: 18044
MD5sum: c1e2bce64a8839b535318dfa1d52dee1
Description: Debian Runlevel configuration tool
 This tool configures system services in connection with system
 runlevels.  It turns on/off services using the scripts in
 /etc/init.d/.  Rcconf works with System-V style runlevel configuration.
 It is a TUI(Text User Interface) frontend to the update-rc.d command.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

