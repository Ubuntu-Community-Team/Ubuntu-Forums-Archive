---
title: "Ubuntu 11.10 and Hibernation in an HP touchsmart tm2"
date: 2012-02-08
forum: Desktop Environments
---

### Post by vedovatti on 2012-02-08
Hi there,

I have problem with Hibernation. It used to work on older version and consequent upgrades of Ubuntu till 11.10, but I had to reinstall the whole system and now the machine does not hibernate properly.

I have a HP touchsmart tm2 Intel i5, hybrid graphics (ATI 5450), 8 GB RAM, WLAN Broadcom 4313 (using property driver "wl". I dedicated a SWAP partition 2 GB to hibernate.

So the computer is fresh installed Ubuntu 11.10 64bit. I have tried using the command *sudo dpkg-reconfigure uswsusp* to reconfigure all ways possible (encrypted, checksum, etc.) and got no luck.

The computer suspends really well. But with hibernation everything goes fine up to the resume. The system resumes it boots and I get the splash boot Ubuntu, saying: *resuming ....* Then the system freezes in the middle of it. The computer is not 100% blocked because I can still turn on and off the wireless and reboot with CTRL + ALT + SUPR. 

So I have been investigating and other similar problem fixed with workarouds. The USB 3.0 gives troubles (but I do not have), the Accelerometer (I tried to add a file with /etc/pm/config.d/AccelerometerSuspend.config *SUSPEND_MODULES="hp_accel lis3lv02d*" that to other people worked but no luck). And I have tried to resume and suspend with both Graphic Cards Intel/ATI both, same result.

Does anybody has a suggestion about this because? I really need hibernation for my everyday work.

Here is a the kernel.log for process of a hibernation, freeze and reboot

Thank you

```
Feb  8 16:13:26 HP-TouchSmart-tm2-Linux sudo: pam_ecryptfs: pam_sm_authenticate: /home/carlos is already mounted
Feb  8 16:13:49 HP-TouchSmart-tm2-Linux kernel: [26694.001027] [UFW BLOCK] IN=eth1 OUT= MAC=00:26:82:bd:17:61:c0:25:06:47:2c:55:08:00 SRC=192.168.178.1 DST=192.168.178.22 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=2659 DF PROTO=TCP SPT=53074 DPT=14013 WINDOW=5840 RES=0x00 SYN URGP=0 
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux NetworkManager[1206]: <info> sleep requested (sleeping: no  enabled: yes)
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux NetworkManager[1206]: <info> sleeping or disabling...
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux NetworkManager[1206]: <info> (eth0): now unmanaged
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux NetworkManager[1206]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux NetworkManager[1206]: <info> (eth0): cleaning up...
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux NetworkManager[1206]: <info> (eth0): taking down device.
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux NetworkManager[1206]: <info> (eth1): now unmanaged
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux NetworkManager[1206]: <info> (eth1): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux NetworkManager[1206]: <info> (eth1): deactivating device (reason 'sleeping') [37]
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux NetworkManager[1206]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1932
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux avahi-daemon[1205]: Withdrawing address record for 192.168.178.22 on eth1.
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux avahi-daemon[1205]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.178.22.
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux avahi-daemon[1205]: Interface eth1.IPv4 no longer relevant for mDNS.
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux NetworkManager[1206]: <info> (eth1): cleaning up...
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux NetworkManager[1206]: <info> (eth1): taking down device.
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux wpa_supplicant[1502]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux avahi-daemon[1205]: Interface eth1.IPv6 no longer relevant for mDNS.
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux avahi-daemon[1205]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::226:82ff:febd:1761.
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux avahi-daemon[1205]: Withdrawing address record for fe80::226:82ff:febd:1761 on eth1.
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux dbus[1163]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Feb  8 16:14:13 HP-TouchSmart-tm2-Linux dbus[1163]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb  8 16:14:14 HP-TouchSmart-tm2-Linux anacron[25688]: Anacron 2.3 started on 2012-02-08
Feb  8 16:14:14 HP-TouchSmart-tm2-Linux anacron[25688]: Normal exit (0 jobs run)
Feb  8 16:14:15 HP-TouchSmart-tm2-Linux kernel: [26720.409340] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
Feb  8 16:14:17 HP-TouchSmart-tm2-Linux avahi-daemon[1205]: Withdrawing workstation service for eth1.
Feb  8 16:14:17 HP-TouchSmart-tm2-Linux NetworkManager[1206]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1/rfkill0 disappeared
Feb  8 16:14:17 HP-TouchSmart-tm2-Linux NetworkManager[1206]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth1, iface: eth1)
Feb  8 16:14:17 HP-TouchSmart-tm2-Linux kernel: [26722.037418] wl 0000:03:00.0: PCI INT A disabled
Feb  8 16:14:17 HP-TouchSmart-tm2-Linux kernel: [26722.866105] PM: Marking nosave pages: 000000000009d000 - 0000000000100000
Feb  8 16:14:17 HP-TouchSmart-tm2-Linux kernel: [26722.866113] PM: Marking nosave pages: 000000009b63f000 - 000000009b7ff000
Feb  8 16:14:17 HP-TouchSmart-tm2-Linux kernel: [26722.866125] PM: Marking nosave pages: 000000009b800000 - 0000000100000000
Feb  8 16:14:17 HP-TouchSmart-tm2-Linux kernel: [26722.867747] PM: Marking nosave pages: 00000001fc000000 - 0000000200000000
Feb  8 16:14:17 HP-TouchSmart-tm2-Linux kernel: [26722.868090] PM: Basic memory bitmaps created
Feb  8 16:16:15 HP-TouchSmart-tm2-Linux kernel: imklog 5.8.1, log source = /proc/kmsg started.
```

AH, and here is the pm-suspend.log:
```
Fri Feb 10 08:26:32 CET 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux HP-TouchSmart-tm2-Linux 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
michael_mic            12612  0 
arc4                   12529  0 
bnep                   18436  2 
rfcomm                 47946  8 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
ip6t_LOG               16974  4 
xt_hl                  12521  6 
ip6t_rt                12558  3 
nf_conntrack_ipv6      13906  7 
nf_defrag_ipv6         13368  1 nf_conntrack_ipv6
dm_crypt               23199  0 
ipt_REJECT             12576  1 
ipt_LOG                12919  5 
parport_pc             36962  0 
ppdev                  17113  0 
xt_multiport           12597  4 
xt_limit               12711  12 
xt_tcpudp              12603  46 
xt_addrtype            12713  4 
xt_state               12578  14 
snd_hda_codec_hdmi     32040  1 
ip6table_filter        12815  1 
ip6_tables             27864  3 ip6t_LOG,ip6t_rt,ip6table_filter
snd_hda_codec_idt      70553  1 
snd_hda_intel          33390  3 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
binfmt_misc            17540  1 
nf_nat_ftp             12704  0 
nf_nat                 25890  1 nf_nat_ftp
nf_conntrack_ipv4      19716  9 nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
snd_hwdep              13668  1 snd_hda_codec
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           82342  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iptable_filter         12810  1 
ip_tables              27473  1 iptable_filter
x_tables               29846  14 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
lib80211_crypt_tkip    17390  0 
snd_seq_midi_event     14899  1 snd_seq_midi
wl                   2568210  0 
uvcvideo               72711  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
wacom                  37975  0 
btusb                  18600  2 
videodev               92992  1 uvcvideo
bluetooth             166112  23 bnep,rfcomm,btusb
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_compat_ioctl32    17083  1 videodev
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
joydev                 17693  0 
mei                    41480  0 
hp_accel               21880  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
lis3lv02d              19888  2 hp_accel
psmouse                73882  0 
hp_wmi                 18092  0 
serio_raw              13166  0 
sparse_keymap          13890  1 hp_wmi
intel_ips              18089  0 
input_polldev          13896  1 lis3lv02d
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  2 
libahci                26861  1 ahci
radeon               1016211  0 
ttm                    76805  1 radeon
wmi                    19256  1 hp_wmi
i915                  567092  8 
r8169                  52788  0 
drm_kms_helper         42558  2 radeon,i915
drm                   236290  6 radeon,ttm,i915,drm_kms_helper
video                  19412  1 i915
i2c_algo_bit           13423  2 radeon,i915
             total       used       free     shared    buffers     cached
Mem:       7986672    1792052    6194620          0      57084    1047352
-/+ buffers/cache:     687616    7299056
Swap:      1819644          0    1819644

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
No PulseAudio daemon running, or not running as session daemon.
Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Fri Feb 10 08:26:36 CET 2012: performing hibernate

```

---

### Post by vedovatti on 2012-02-10
I can mark it as solved. As a work around I installed the PPA: tuxonice/ppa

Installed Tuxonice

The hibernation works!

---

