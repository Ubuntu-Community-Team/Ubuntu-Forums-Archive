---
title: "Accidentally deleted init.d"
date: 2006-08-09
forum: Desktop Environments
---

### Post by straylite on 2006-08-09
Hi all

Well, I think I claim the prize for stupidest thing to do with a linux distribution.

I was trying to fix my soundcard, by trying:

rm -f /var/lib/alsa/asound.conf && blah blah

but actually typed

rm -f /var/lib/alsa/asound.conf ** blah blah

whilst in my /etc/init.d folder, therefore wiping the contents. :) 

My system is 6.06 and I have access to a 5.x version (I'm not sure how you find out what release you have) so I've copied back the base set of init.d scripts but I'm still missing a few.

My questions are:

(a) is there an easy way to put these files back, by doing a 'repair' or some other operation

(b) how can I upgrade my 5.x system to 6.06 so I get the latest init.d files

(c) should I just dig through my current active 6.06 system and try and find the scripts?

Thanks,

j.

---

### Post by mlind on 2006-08-09
> **straylite said:**
> Hi all

Well, I think I claim the prize for stupidest thing to do with a linux distribution.

I was trying to fix my soundcard, by trying:

rm -f /var/lib/alsa/asound.conf && blah blah

but actually typed

rm -f /var/lib/alsa/asound.conf ** blah blah

whilst in my /etc/init.d folder, therefore wiping the contents. :) 

My system is 6.06 and I have access to a 5.x version (I'm not sure how you find out what release you have) so I've copied back the base set of init.d scripts but I'm still missing a few.

My questions are:

(a) is there an easy way to put these files back, by doing a 'repair' or some other operation

(b) how can I upgrade my 5.x system to 6.06 so I get the latest init.d files

(c) should I just dig through my current active 6.06 system and try and find the scripts?

Thanks,

j.

Don't boot or you're about to have very broken system .. :D

a) initscripts in /etc/init.d are provided by separate packages. You must reinstall these to get the scripts back. If **aptitude reinstall** doesn't work, you must first purge - then install.

Here are the packages that provide initscripts to my /etc/init.d/
```

$ dpkg -S /etc/init.d/*
acpid: /etc/init.d/acpid
acpi-support: /etc/init.d/acpi-support
alsa-utils: /etc/init.d/alsa-utils
anacron: /etc/init.d/anacron
apache2-common: /etc/init.d/apache2
apmd: /etc/init.d/apmd
at: /etc/init.d/atd
binfmt-support: /etc/init.d/binfmt-support
bittorrent: /etc/init.d/bittorrent
bluez-utils: /etc/init.d/bluez-utils
initscripts: /etc/init.d/bootclean.sh
initscripts: /etc/init.d/bootlogd
initscripts: /etc/init.d/bootmisc.sh
brltty: /etc/init.d/brltty
initscripts: /etc/init.d/checkfs.sh
initscripts: /etc/init.d/checkroot.sh
console-tools: /etc/init.d/console-screen.sh
cron: /etc/init.d/cron
cupsys: /etc/init.d/cupsys
dbus: /etc/init.d/dbus
pppconfig: /etc/init.d/dns-clean
evms: /etc/init.d/evms
festival: /etc/init.d/festival
firestarter: /etc/init.d/firestarter
gdm: /etc/init.d/gdm
libc6: /etc/init.d/glibc.sh
gpm: /etc/init.d/gpm
initscripts: /etc/init.d/halt
hdparm: /etc/init.d/hdparm
initscripts: /etc/init.d/hostname.sh
hotkey-setup: /etc/init.d/hotkey-setup
hplip: /etc/init.d/hplip
util-linux: /etc/init.d/hwclock.sh
console-common: /etc/init.d/keymap.sh
klogd: /etc/init.d/klogd
laptop-mode-tools: /etc/init.d/laptop-mode
linux-restricted-modules-common: /etc/init.d/linux-restricted-modules-common
ifupdown: /etc/init.d/loopback
lvm-common: /etc/init.d/lvm
makedev: /etc/init.d/makedev
mdadm: /etc/init.d/mdadm
mdadm: /etc/init.d/mdadm-raid
module-init-tools: /etc/init.d/module-init-tools
initscripts: /etc/init.d/mountall.sh
initscripts: /etc/init.d/mountdevsubfs
initscripts: /etc/init.d/mountvirtfs
initscripts: /etc/init.d/mtab
netbase: /etc/init.d/networking
nvidia-kernel-common: /etc/init.d/nvidia-kernel
pcmcia-cs: /etc/init.d/pcmcia
pcmciautils: /etc/init.d/pcmciautils
postfix: /etc/init.d/postfix
powernowd: /etc/init.d/powernowd
powernowd: /etc/init.d/powernowd.early
ppp: /etc/init.d/ppp
ppp: /etc/init.d/pppd-dns
procps: /etc/init.d/procps.sh
sysv-rc: /etc/init.d/rc
initscripts: /etc/init.d/rc.local
sysv-rc: /etc/init.d/rcS
readahead: /etc/init.d/readahead
readahead: /etc/init.d/readahead-desktop
sysv-rc: /etc/init.d/README
initscripts: /etc/init.d/reboot
initscripts: /etc/init.d/rmnologin
rsync: /etc/init.d/rsync
schroot: /etc/init.d/schroot
screen: /etc/init.d/screen
initscripts: /etc/init.d/sendsigs
initscripts: /etc/init.d/single
initscripts: /etc/init.d/skeleton
openssh-server: /etc/init.d/ssh
initscripts: /etc/init.d/stop-bootlogd
readahead: /etc/init.d/stop-readahead
sysklogd: /etc/init.d/sysklogd
udev: /etc/init.d/udev
initscripts: /etc/init.d/umountfs
initscripts: /etc/init.d/umountnfs.sh
initscripts: /etc/init.d/umountroot
initscripts: /etc/init.d/urandom
usplash: /etc/init.d/usplash
acpi-support: /etc/init.d/vbesave
initscripts: /etc/init.d/waitnfs.sh
x11-common: /etc/init.d/x11-common

```


To reinstall a package
```

sudo aptitude reinstall *package*

```

This doesn't usually replace "important" files, like configuration files on /etc folder. In this case (probably) you need to purge the package first, then install.

```

sudo dpkg -P **--force-depends** *package*
sudo aptitude install *package*

```

Don't install a package that insn't already installed on your system.



You could also use **debootstrap** to make a fake Ubuntu install to somewhere in your partition and get most of the vitral initscripts from there
```

mkdir /tmp/dapper
sudo debootstrap dapper /tmp/dapper http://archive.ubuntu.com/ubuntu

```

---

