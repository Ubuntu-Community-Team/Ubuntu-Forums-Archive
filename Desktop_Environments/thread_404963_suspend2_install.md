---
title: "suspend2 install"
date: 2007-04-09
forum: Desktop Environments
---

### Post by stavpal on 2007-04-09
Hi, I've patched my kernel (2.6.20.6) with suspend2, rebooted etc and now I'm trying to install the script. Thing is, when I try to, I get this:
```

stavpal@stavpal:/tmp/hibernate-script-1.94$ ./install.sh
Config directory /etc/hibernate and/or /usr/local/sbin/hibernate already exist.
Are you sure you want to overwrite them? (y/N) y

Installing hibernate script to /usr/local/sbin/hibernate ...
Installing configuration files to /etc/hibernate ...
  **
  ** You already have a configuration file at /etc/hibernate/hibernate.conf
  ** The new version will be installed to /etc/hibernate/hibernate.conf.dist
  **
cp: cannot stat `ususpend.conf': No such file or directory
Install aborted due to errors.

```

I've added the line "deb [http://cp.yi.org/apt/hibernate](http://cp.yi.org/apt/hibernate) ./" in sources.list

when I tried to suspend I got a 
```

Some modules failed to unload: nvidia
hibernate: Aborting suspend due to errors in ModulesUnloadBlacklist (use --force to override).

```

nvidia is added in the "blacklisted-modules" file

```

# 
# WARNING: No attempt is made to preserve this file upon upgrades.
#          The file format may also change between hibernate script versions.
#          It is recommended that you enter any modules you wish to unload
#          into hibernate.conf.
# 
# The syntax of each line in this file is "module name [...]" where [...] is
# a sequence of minimum/maximum kernel version pairs that the module is
# incompatible with. For example:
#     usb-ehci 2.4.0 2.4.25 2.6.0 2.6.2
# (would indicate that usb-ehci was incompatible in 2.4 until 2.4.25, and in
# 2.6 until 2.6.2 - example only!)
#
# A module without any versions is always considered unsuspendable.
#
# If a line is prefixed with an '@' sign, then the versions are interpreted
# as the module version (as reported by modinfo) instead of the kernel version.
# Unversioned modules (modules with no version: line shown in modinfo) are
# always unloaded if listed, regardless of the version range.
#
# This format has some limitations - it does not take into account Software
# Suspend 2 versions (which may include driver updates).
#

nvidia
acx100
acx_pci
hsfmodem
prism54

bcm4400		2.6.0	2.6.99
emu10k1		2.4.0	2.4.99	2.6.0	2.6.99
forcedeth	2.4.0	2.4.99	2.6.0	2.6.99
@ipw2100	0.0	1.0.2
@ipw2200	0.0	0.20
natsemi		2.6.0	2.6.99
psmouse		2.6.0	2.6.99
rt2400		2.4.0	2.4.99	2.6.0	2.6.99
ehci_hcd	2.6.0	2.6.14
ohci_hcd	2.6.0	2.6.14
uhci_hcd	2.6.0	2.6.14
ehci-hcd	2.4.0	2.4.99
usb-ohci	2.4.0	2.4.99
usb-uhci	2.4.0	2.4.99
snd_ens1370	2.6.0	2.6.99
snd_ens1371	2.6.0	2.6.99
snd_maestro3	2.6.0	2.6.99
snd_bt_sco	2.6.0	2.6.99
en1370		2.6.0	2.6.99
en1371		2.6.0	2.6.99
via_agp		2.6.0	2.6.8
via_rhine	2.6.0	2.6.99
i8042		2.6.10	2.6.99
intel_mch_agp	2.6.0	2.6.99
rt2500		2.6.0	2.6.99

button		2.6.9	2.6.99
speedstep_smi	2.6.12	2.6.99

@ndiswrapper    0.10    0.11

```

Do I need to disable agpgart before compiling the kernel? (So that the kernel has agpgart disabled I mean - I read it here [http://forums.gentoo.org/viewtopic-p-1995227.html](http://forums.gentoo.org/viewtopic-p-1995227.html))

---

### Post by Nigel_C on 2007-04-10
Hi.

I'm not an NVidia user myself, but I understand that's what you do need to do. See, for example,
[http://lists.suspend2.net/lurker/message/20070410.034944.07a992b1.en.html](http://lists.suspend2.net/lurker/message/20070410.034944.07a992b1.en.html).

Regards,

Nigel

---

### Post by stavpal on 2007-04-10
well that's an old chipset. I as wrote above, I read similar thing about disabling apggart in the kernel and enabling "nvagp" in xorg.conf

If it helps, my specs are: p4 1.9GHz, 512MB rdram, asus p4t-e mobo (850 chipset), nvidia 6600gt agp, sb audigy etc...

---

