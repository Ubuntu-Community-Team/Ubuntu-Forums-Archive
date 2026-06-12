---
title: "error processing linux-ubuntu-modules-2.6.24-21-generic"
date: 2009-02-21
forum: General Help
---

### Post by sujahat on 2009-02-21
Hi Every one..

I need some help... did search for a solution.. came down to the grub.. I know it has something to do with booting ubuntu.. I am using 8.04...
The thing is I am on Dual boot with Vista..
I used the link CD and installed Ubuntu from with ion Vista that was months ago... I us Vista for gaming.... and heard of Flatout2 with wine.. so logged in to my old dualboot ubuntu that I dont use much.. unless I am free and want to mess around.. 

either ways.. this is what I have,..

Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-20-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... /usr/sbin/update-grub: line 1413: /boot/grub/menu.lst: Operation not supported
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-23-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-21-generic:
 linux-ubuntu-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-23-generic:
 linux-ubuntu-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-23-generic; however:
  Package linux-ubuntu-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-23-generic:
 linux-restricted-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-23-generic; however:
  Package linux-restricted-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.23.25); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.23.25); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-21-generic:
 linux-restricted-modules-2.6.24-21-generic depends on linux-image-2.6.24-21-generic; however:
  Package linux-image-2.6.24-21-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-21-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
 linux-image-2.6.24-21-generic
 linux-image-2.6.24-23-generic
 linux-ubuntu-modules-2.6.24-21-generic
 linux-ubuntu-modules-2.6.24-23-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-23-generic
 linux-restricted-modules-generic
 linux-generic
 linux-restricted-modules-2.6.24-21-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


And my Grub is

#!/bin/sh
#
# Wrapper to warn user about kernel-img.conf move
#

if grep -q '  */sbin/update-grub$' /etc/kernel-img.conf 2> /dev/null ; then
	cat >&2 <<EOF
Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1]
file and follow its instructions.

 1. /usr/share/doc/grub/NEWS.Debian.gz


EOF
fi

if [ -x /usr/sbin/update-grub ]; then
	exec /usr/sbin/update-grub "$@"
else
	echo "Your /usr is broken, please fix it before call this wrapper!" >&2
fi

Any idea??

---

