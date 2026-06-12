---
title: "Error on start-up"
date: 2005-07-24
forum: Desktop Environments
---

### Post by GrootBrak on 2005-07-24
I got this error as soon as the Desktop starts. 

> Error activating XKB configuration.
Probably internal X server problem.

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/xkb 

Any ideas for fixing it? Looks like it has something to do with my keyboard, but so far everything seems to work. Except for my sound, never had a single sound from Ubuntu... Could the above be the reason?

---

### Post by Natja on 2005-07-24
You should probably file it as a bug on ubuntu bugzilla ( [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com) )

---

### Post by LazyIvan on 2005-07-27
I have the same error message but my sound works, as does everything else (at least everything else that I use).  For all I can tell, this error does not impact my system at all, it just adds the inconvenience of clicking away the message with every boot.

---

### Post by charlieg on 2005-07-27
Can anybody provide the log from /var/log/Xorg.0.log from a fresh boot.

[quote="GrootBrak"]never had a single sound from Ubuntu... Could the above be the reason?[/quote]
No.  It's totally unrelated. XKB is associated with keyboard handling.

Have you ever tried to diagnose your sound problem?  Could you post the output of the following command:
```
$ lsmod
```

---

### Post by LazyIvan on 2005-07-27
Here is a link to my (entire) log file from a fresh boot, not too sure what lines are unnecessary so i left it all in... I am having the same problem as the original poster, just without the sound issue.

[Xorg.0.log](http://www.uweb.ucsb.edu/~cabair)

---

### Post by GrootBrak on 2005-08-01
[QUOTE=charlieg]Can anybody provide the log from /var/log/Xorg.0.log from a fresh boot.


No.  It's totally unrelated. XKB is associated with keyboard handling.

Have you ever tried to diagnose your sound problem?  Could you post the output of the following command:
```
$ lsmod
```[/QUOTE]
 Thanx. keyboard was wrong, working fine now. Solved it by accident!!!
Here is output for lsmod

jacques@HomePC:/Alsa_new/alsa-driver-1.0.9b $ lsmod
Module                  Size  Used by
isofs                  33976  0
udf                    79876  0
ppp_deflate             6144  0
zlib_deflate           20760  1 ppp_deflate
bsd_comp                5888  0
ppp_async              10624  1
crc_ccitt               2432  1 ppp_async
ppp_generic            27668  7 ppp_deflate,bsd_comp,ppp_async
slhc                    7040  1 ppp_generic
rfcomm                 34588  7
l2cap                  23300  7 rfcomm
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ipv6                  230020  10
lp                     10436  0
button                  6936  0
ac                      5132  0
battery                 9740  0
e100                   30208  0
mii                     4864  1 e100
ata_piix                7940  0
libata                 36356  1 ata_piix
scsi_mod              115148  1 libata
ehci_hcd               27780  0
hci_usb                12928  4
bluetooth              44036  9 rfcomm,l2cap,hci_usb
usblp                  12032  1
uhci_hcd               29328  0
usbcore               104292  7 ehci_hcd,hci_usb,usblp,uhci_hcd
shpchp                 87276  0
pciehp                 83948  0
pci_hotplug            30640  2 shpchp,pciehp
parport_pc             32064  1
parport                37320  2 lp,parport_pc
floppy                 54996  0
pcspkr                  3816  0
tsdev                   7168  0
mousedev               10124  2
psmouse                17800  0
rtc                    12216  0
evdev                   9088  0
nls_utf8                2304  2
ntfs                   88660  2
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
siimage                12032  1
piix                   12576  1
ide_disk               16768  7
ide_core              125272  4 ide_generic,siimage,piix,ide_disk
unix                   25904  751
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb


As you can see, no sound, please check my frustrations under harware!!!

---

