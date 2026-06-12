---
title: "System hangs when returning from hibernate but not sleep (12.04)"
date: 2012-07-17
forum: Desktop Environments
---

### Post by juliushibert63 on 2012-07-17
I'm running Ubuntu 12.04 on a Acer Revo r3610 and when ever I set the machine to hibernate via the command line using 

```
sudo pm-hibernate
```

The machine hibernates successfully but then upon waking it via WOL the machine starts too boot and then hangs before ever getting to the first Ubuntu Desktop screen.

I can still access the machine via the command line through CTRL+ALT+F3 (I think that's the correct key combo) or via SSH however if I then reboot the machine via....

```
sudo shutdown -r now
```

then the machine reboots but hangs at the GRUB menu asking me to select an OS to boot to. I only have Ubuntu 12.04 on the system. This is extremely annoying if I'm working remotely on the machine via SSH.

The odd thing is if I set the machine to sleep/suspend instead using the command line and 

```
sudo pm-suspend
```

and wake the machine via the same WOL command it wakes fine with no problems.

---

### Post by juliushibert63 on 2012-07-18
I don't know if this helps but here is the output of lscpi:

```
$ lspci
00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: NVIDIA Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: NVIDIA Corporation ION VGA (rev b1)
05:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
```


I've also checked /var/log/ and there's no pm-hibernate.log files only these:

```
$ ls -ltr pm-*
-rw-r--r-- 1 root root  13K Mar 31 13:43 pm-suspend.log.4.gz
-rw-r--r-- 1 root root 2.4K Mar 31 13:43 pm-powersave.log.4.gz
-rw-r--r-- 1 root root  11K Apr 30 20:25 pm-suspend.log.3.gz
-rw-r--r-- 1 root root 2.3K May  1 07:41 pm-powersave.log.3.gz
-rw-r--r-- 1 root root 7.7K Jun  3 12:29 pm-suspend.log.2.gz
-rw-r--r-- 1 root root 1.6K Jun  3 12:29 pm-powersave.log.2.gz
-rw-r--r-- 1 root root 376K Jul  2 00:14 pm-suspend.log.1
-rw-r--r-- 1 root root 280K Jul  2 10:02 pm-powersave.log.1
-rw-r--r-- 1 root root 142K Jul 18 11:53 pm-powersave.log
-rw-r--r-- 1 root root 212K Jul 18 11:53 pm-suspend.log
```

---

### Post by juliushibert63 on 2012-07-24
-Bump-

Here's also the contents of pm-supsend.log:

```
Initial commandline parameters: 
Tue Jul  3 20:05:37 BST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux htpc-tv 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:33:05 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31418  0 
ntfs                  100171  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55605  2 vfat,msdos
jfs                   175085  0 
xfs                   747494  0 
reiserfs              230896  0 
ext2                   67987  0 
des_generic            21191  0 
md4                    12523  0 
bnep                   17830  2 
rfcomm                 38139  2 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13516  1 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174055  1 
nls_utf8               12493  0 
cifs                  257941  0 
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
xt_tcpudp              12531  26 
xt_addrtype            12596  4 
xt_state               12514  14 
joydev                 17393  1 
usbhid                 41906  0 
ums_realtek            17920  0 
uas                    17828  0 
snd_hda_intel          32765  4 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
nvidia               9874792  40 
hid                    77367  1 usbhid
snd_seq_midi           13132  0 
psmouse                87213  0 
snd_rawmidi            25424  1 snd_seq_midi
ip6table_filter        12711  1 
snd_seq_midi_event     14475  1 snd_seq_midi
ip6_tables             18432  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd                    62064  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21974  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
k10temp                12990  0 
serio_raw              13027  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
shpchp                 32325  0 
video                  19068  0 
wmi                    18744  0 
mac_hid                13077  0 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  1 ums_realtek
forcedeth              58096  0 
pata_amd               13750  0 
             total       used       free     shared    buffers     cached
Mem:       1802192    1501712     300480          0     234824     613756
-/+ buffers/cache:     653132    1149060
Swap:      3905532       6844    3898688

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Jul  3 20:05:42 BST 2012: performing suspend
fbcon fb0 state 1
fbcon fb0 state 0
Tue Jul  3 23:15:54 BST 2012: Awake.
Tue Jul  3 23:15:54 BST 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Initial commandline parameters: 
Wed Jul 11 22:24:46 BST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux htpc-tv 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
des_generic            21191  0 
md4                    12523  0 
bnep                   17830  2 
rfcomm                 38139  2 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
nls_utf8               12493  0 
cifs                  257941  0 
binfmt_misc            17292  1 
vesafb                 13516  1 
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
xt_tcpudp              12531  26 
xt_addrtype            12596  4 
xt_state               12514  14 
snd_hda_codec_hdmi     31775  1 
ip6table_filter        12711  1 
ip6_tables             18432  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nvidia               9874792  40 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_hda_codec_realtek   174055  1 
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21974  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_hda_intel          32765  4 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
k10temp                12990  0 
snd_rawmidi            25424  1 snd_seq_midi
joydev                 17393  1 
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                87213  0 
serio_raw              13027  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  0 
shpchp                 32325  0 
video                  19068  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
ums_realtek            17920  0 
usb_storage            39646  1 ums_realtek
uas                    17828  0 
forcedeth              58096  0 
pata_amd               13750  0 
             total       used       free     shared    buffers     cached
Mem:       1802212    1306092     496120          0      77164     695684
-/+ buffers/cache:     533244    1268968
Swap:      3905532        160    3905372

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Initial commandline parameters: 
Sat Jul 21 10:12:05 BST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux htpc-tv 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
rfcomm                 38139  2 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
binfmt_misc            17292  1 
vesafb                 13516  1 
nvidia               9874792  40 
snd_hda_codec_hdmi     31775  1 
nls_utf8               12493  0 
cifs                  257941  0 
snd_hda_codec_realtek   174055  1 
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
xt_tcpudp              12531  26 
xt_addrtype            12596  4 
xt_state               12514  14 
ip6table_filter        12711  1 
ip6_tables             18432  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21974  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
psmouse                87213  0 
serio_raw              13027  0 
k10temp                12990  0 
shpchp                 32325  0 
snd_hda_intel          32765  4 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
video                  19068  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  0 
snd_timer              28931  2 snd_pcm,snd_seq
mac_hid                13077  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
uas                    17828  0 
forcedeth              58096  0 
pata_amd               13750  0 
usb_storage            39646  1 ums_realtek
             total       used       free     shared    buffers     cached
Mem:       1802212    1552408     249804          0     315372     553232
-/+ buffers/cache:     683804    1118408
Swap:      3905532       3096    3902436

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Jul 21 10:12:08 BST 2012: performing suspend
fbcon fb0 state 1
fbcon fb0 state 0
Sat Jul 21 11:09:46 BST 2012: Awake.
Sat Jul 21 11:09:46 BST 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Initial commandline parameters: 
Sat Jul 21 11:14:33 BST 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux htpc-tv 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
rfcomm                 38139  2 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
binfmt_misc            17292  1 
vesafb                 13516  1 
nvidia               9874792  40 
snd_hda_codec_hdmi     31775  1 
nls_utf8               12493  0 
cifs                  257941  0 
snd_hda_codec_realtek   174055  1 
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
xt_tcpudp              12531  26 
xt_addrtype            12596  4 
xt_state               12514  14 
ip6table_filter        12711  1 
ip6_tables             18432  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21974  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
psmouse                87213  0 
serio_raw              13027  0 
k10temp                12990  0 
shpchp                 32325  0 
snd_hda_intel          32765  2 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
video                  19068  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  0 
snd_timer              28931  2 snd_pcm,snd_seq
mac_hid                13077  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
uas                    17828  0 
forcedeth              58096  0 
pata_amd               13750  0 
usb_storage            39646  1 ums_realtek
             total       used       free     shared    buffers     cached
Mem:       1802212    1540676     261536          0     201576     617996
-/+ buffers/cache:     721104    1081108
Swap:      3905532       6104    3899428

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Jul 21 11:14:37 BST 2012: performing suspend
fbcon fb0 state 1
fbcon fb0 state 0
Sat Jul 21 14:12:34 BST 2012: Awake.
Sat Jul 21 14:12:34 BST 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Initial commandline parameters: 
Mon Jul 23 22:44:55 BST 2012: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux htpc-tv 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 16:26:01 UTC 2012 i686 athlon i386 GNU/Linux
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  2 
bluetooth             158438  10 bnep,rfcomm
binfmt_misc            17292  1 
vesafb                 13516  1 
snd_hda_codec_hdmi     31775  1 
nls_utf8               12493  0 
cifs                  257941  0 
snd_hda_codec_realtek   174055  1 
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
xt_tcpudp              12531  26 
xt_addrtype            12596  4 
xt_state               12514  14 
nvidia               9874792  40 
joydev                 17393  1 
ip6table_filter        12711  1 
ip6_tables             18432  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
snd_hda_intel          32765  4 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ip_tables              18106  1 iptable_filter
x_tables               21974  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
psmouse                87213  0 
serio_raw              13027  0 
k10temp                12990  0 
snd_pcm                80845  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
usbhid                 41906  0 
video                  19068  0 
shpchp                 32325  0 
hid                    77367  1 usbhid
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
uas                    17828  0 
usb_storage            39646  1 ums_realtek
forcedeth              58096  0 
pata_amd               13750  0 
             total       used       free     shared    buffers     cached
Mem:       1802212    1655536     146676          0     226788     895592
-/+ buffers/cache:     533156    1269056
Swap:      3905532       1160    3904372

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
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
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:

/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Mon Jul 23 22:45:00 BST 2012: performing hibernate
Mon Jul 23 22:46:16 BST 2012: Awake.
Mon Jul 23 22:46:16 BST 2012: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:

/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:
```

---

