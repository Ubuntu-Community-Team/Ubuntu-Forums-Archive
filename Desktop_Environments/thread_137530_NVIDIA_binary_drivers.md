---
title: "NVIDIA binary drivers"
date: 2006-02-28
forum: Desktop Environments
---

### Post by Alendit on 2006-02-28
Hi, folks.

I know this is quite stupid thema, but i've got problems with nvidia drivers from nvidia.com.

I used HOWTO to install the driver, and it seems to work, but after 2-3 restarts X-server does not start(a half of screen is white, a half is black, after 5 sec is all screen black). If i boot in rescue mode and reinstall the drivers, i works again. But after 2-3 restarts a still have the same problem. I user NVIDIA autoconfig utility to config xorg.conf. I removed nvidia-glx and another to nvidia related ubuntu packges. I really have no idea why i've got this problem.

There one more problem. I would like to use standart ubuntu drivers, but these don't give any 3d perfomance on my system - 3ddesk doesn't work, and opengl screensavers to. With nvidia driver it works ok.

Alendit

---

### Post by RickvanderZwet on 2006-02-28
Hi, this is a problem with the startup scripts (placing bad symlinks) Could you copy 
ls -1 /etc/init.d for me (lost the name of the script responsible)

---

### Post by Alendit on 2006-02-28
2RickvanderZwet
```

ln -1 /etc/init.d

acpid
acpi-support
alsa
alsa-utils
anacron
apmd
atd
bluez-utils
bootclean.sh
bootlogd
bootmisc.sh
checkfs.sh
checkroot.sh
console-screen.sh
cron
cupsys
dbus
dns-clean
evms
fetchmail
gdm
halt
hdparm
hostname.sh
hotkey-setup
hotplug
hotplug-net
hplip
hsf
hwclockfirst.sh
hwclock.sh
ifrename
ifupdown
ifupdown-clean
keymap.sh
klogd
linux-restricted-modules-common
lvm
makedev
mdadm
mdadm-raid
module-init-tools
mountall.sh
mountnfs.sh
mountvirtfs
nethack-common
networking
ntpdate
pcmcia
powernowd
ppp
pppd-dns
procps.sh
rc
rcS
readahead
README
reboot
rmnologin
rsync
screen-cleanup
sendsigs
single
skeleton
stop-bootlogd
sudo
sysklogd
udev
udev-mtab
umountfs
umountnfs.sh
urandom
usplash
vbesave
xorg-common
```

I think i know what are you looking for. I've removed a file "nvidia-glx" today with "complete uninstall". The system seems to be stabil. When it will be no problems this threat can be marked as solved.

Thanks for the support.

Alendit

---

