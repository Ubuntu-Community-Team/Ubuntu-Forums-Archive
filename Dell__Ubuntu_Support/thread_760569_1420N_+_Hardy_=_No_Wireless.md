---
title: "1420N + Hardy = No Wireless"
date: 2008-04-20
forum: Dell  Ubuntu Support
---

### Post by mlsquad on 2008-04-20
I have a Dell 1420N that came with Feisty preinstalled.  Wireless always worked in both Feisty and Gutsy.  I just upgraded to Hardy Beta, and now my wireless does not work.  When I first boot up NetworkManager shows my wireless network.  If I run *iwlist scan* it shows my wireless network.  After about 15 seconds after bootup *iwlist scan* no longer shows my wireless network, and neither does NetworkManager.
The only way I can get it online is through a wired connection.  Anyone have any ideas on where to start looking?

---

### Post by mlsquad on 2008-04-20
Here's some output that may help.

# :~$ lspci | grep Wireless  
# 0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)  
# :~$ lsmod  
# Module                  Size  Used by  
# ipv6                  267780  12   
# i915                   32512  2   
# drm                    82580  3 i915  
# af_packet              23812  2   
# rfcomm                 41744  2   
# l2cap                  25728  13 rfcomm  
# bluetooth              61156  4 rfcomm,l2cap  
# ppdev                  10372  0   
# acpi_cpufreq           10796  2   
# cpufreq_conservative     8712  0   
# cpufreq_powersave       2688  0   
# cpufreq_stats           7104  0   
# cpufreq_ondemand        9740  1   
# freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand  
# cpufreq_userspace       5284  0   
# container               5632  0   
# sbs                    15112  0   
# dock                   11280  0   
# sbshc                   7680  1 sbs  
# iptable_filter          3840  0   
# ip_tables              14820  1 iptable_filter  
# x_tables               16132  1 ip_tables  
# arc4                    2944  2   
# ecb                     4480  2   
# blkcipher               8324  1 ecb  
# sbp2                   24072  0   
# parport_pc             36260  0   
# lp                     12324  0   
# parport                37832  3 ppdev,parport_pc,lp  
# joydev                 13120  0   
# iwl3945                89844  0   
# iwlwifi_mac80211      219108  1 iwl3945  
# snd_hda_intel         344600  3   
# cfg80211               15112  1 iwlwifi_mac80211  
# snd_pcm_oss            42144  0   
# snd_mixer_oss          17920  1 snd_pcm_oss  
# sr_mod                 17956  0   
# cdrom                  37408  1 sr_mod  
# snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss  
# snd_page_alloc         11400  2 snd_hda_intel,snd_pcm  
# snd_hwdep              10500  1 snd_hda_intel  
# snd_seq_dummy           4868  0   
# snd_seq_oss            35584  0   
# snd_seq_midi            9376  0   
# snd_rawmidi            25760  1 snd_seq_midi  
# snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi  
# snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
# serio_raw               7940  0   
# video                  19856  0   
# output                  4736  1 video  
# ricoh_mmc               4352  0   
# snd_timer              24836  2 snd_pcm,snd_seq  
# snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
# ac                      6916  0   
# sdhci                  19076  0   
# snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device  
# battery                14212  0   
# mmc_core               51460  1 sdhci  
# wmi_acer                9644  0   
# button                  9232  0   
# shpchp                 34452  0   
# iTCO_wdt               13092  0   
# iTCO_vendor_support     4868  1 iTCO_wdt  
# evdev                  13056  8   
# pci_hotplug            30880  1 shpchp  
# soundcore               8800  1 snd  
# dcdbas                  9504  0   
# intel_agp              25492  1   
# agpgart                34760  3 drm,intel_agp  
# pcspkr                  4224  0   
# psmouse                40336  0   
# ext3                  136712  1   
# jbd                    48404  1 ext3  
# mbcache                 9600  1 ext3  
# sg                     36880  0   
# sd_mod                 30720  3   
# ata_piix               19588  0   
# ata_generic             8324  0   
# ohci1394               33584  0   
# ahci                   28420  2   
# pata_acpi               8320  0   
# ieee1394               93752  2 sbp2,ohci1394  
# libata                159344  4 ata_piix,ata_generic,ahci,pata_acpi  
# scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata  
# tg3                   116228  0   
# ehci_hcd               37900  0   
# uhci_hcd               27024  0   
# usbcore               146028  3 ehci_hcd,uhci_hcd  
# thermal                16796  0   
# processor              36872  4 acpi_cpufreq,thermal  
# fan                     5636  0   
# fbcon                  42912  0   
# tileblit                3456  1 fbcon  
# font                    9472  1 fbcon  
# bitblit                 6784  1 fbcon  
# softcursor              3072  1 bitblit  
# fuse                   50580  5

---

### Post by trooperchix on 2008-04-20
Screw network manager, is there a version of WICD for Hardy?  I had similar issues with my update from Feisty to Gutsy then changed to Wicd and everything has been hunky dory since.  Give it a shot.

:guitar:

---

### Post by mlsquad on 2008-04-20
> **trooperchix said:**
> Screw network manager, is there a version of WICD for Hardy?  I had similar issues with my update from Feisty to Gutsy then changed to Wicd and everything has been hunky dory since.  Give it a shot.

:guitar:

I just tried wicd and it had the same problem.  This is not a NM problem, because I can't even get it to work from the command line.

---

### Post by mlsquad on 2008-04-20
Apparently this is a problem with the wireless driver in Hardy.  [https://bugs.edge.launchpad.net/linux/+bug/185470](https://bugs.edge.launchpad.net/linux/+bug/185470)

---

### Post by sdennie on 2008-04-20
Were you previously using the default ipw3945 driver in Gutsy?  If so, Hardy has switched to the iwl3945 and you may have a stale entry for the old driver in /etc/udev/rules.d/70-persistent-net.rules.  If you see something in that file that says anything about "ipw3945", comment out the next line and reboot.

---

### Post by mlsquad on 2008-04-20
> **vor said:**
> Were you previously using the default ipw3945 driver in Gutsy?  If so, Hardy has switched to the iwl3945 and you may have a stale entry for the old driver in /etc/udev/rules.d/70-persistent-net.rules.  If you see something in that file that says anything about "ipw3945", comment out the next line and reboot.
This install is a fresh Hardy install, not an upgrade.  Here is the output from that file:
[INDENT]david@david-laptop-dell:~$ cat /etc/udev/rules.d/70-persistent-net.rules 
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x1713 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1c:23:f8:ba:80", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1c:bf:51:f9:92", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
[/INDENT]

---

### Post by sdennie on 2008-04-20
Ahhh.  That looks correct.  Did you install the Hardy Beta or RC?  I had problems with wireless with the same card on the Beta but, it seems fixed now (no wireless problems at all now).  I'm not sure if the RC has the fix but, if you can get connect with a cable and download all the updates, it should hopefully fix the card.

---

### Post by mlsquad on 2008-04-20
> **vor said:**
> Ahhh.  That looks correct.  Did you install the Hardy Beta or RC?  I had problems with wireless with the same card on the Beta but, it seems fixed now (no wireless problems at all now).  I'm not sure if the RC has the fix but, if you can get connect with a cable and download all the updates, it should hopefully fix the card.

I thought the Beta was the RC.  Oops.  Installing the Beta and then getting all the updates should put me on RC, no?  If not, then I will download the RC iso, burn, and reinstall.

---

### Post by sdennie on 2008-04-20
If you've already downloaded and installed the beta and can connect via a cable to get the latest update, there is no reason to download and install the RC.  The beta should update to the current packages without a problem.

---

