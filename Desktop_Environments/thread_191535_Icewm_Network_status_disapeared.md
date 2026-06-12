---
title: "Icewm: Network status disapeared"
date: 2006-06-07
forum: Desktop Environments
---

### Post by dskloet on 2006-06-07
Hi,

Since I upgraded to Dapper, icewm stopped showing my network status on the taskbar. I can get it back by changing NetworkStatusDevice in the preferences to "lo" instead of "eth1", but ofcourse that's not the device I want to monitor. Any idea what could be wrong or how to fix this?

thanks,
David

PS. I wasn't sure about the Tag, I have Gnome installed but I rarely use it.

---

### Post by sajochin on 2006-06-19
There seems to be a buggy debian patch to the original IceWM sources, that makes IceWM only display the status of ipv6 devices.
You can remove the return false; statement in line 45 of icewm-1.2.23/debian/patches/ipv6_monitor.dpatch in the sources and recompile icewm.

Just do something like:
$ apt-get source --download-only icewm
$ dpkg-source -x icewm_1.2.23-3ubuntu1.dsc
$ sed -i 's/+ *return false;/+/' icewm-1.2.23/debian/patches/ipv6_monitor.dpatch
$ cd icewm-1.2.23; dpkg-buildpackage -rfakeroot; cd ..
$ sudo dpkg -i icewm_1.2.23-3ubuntu1_i386.deb

---

### Post by dskloet on 2006-06-19
I noticed the network status is displayed about half of the times I return from hibernation. Could it be that my network device is ipv6 about half of the time? ;)

Thanks for the patch.

---

