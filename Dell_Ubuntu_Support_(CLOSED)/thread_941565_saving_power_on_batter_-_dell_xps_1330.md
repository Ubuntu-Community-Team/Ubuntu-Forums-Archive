---
title: "saving power on batter - dell xps 1330"
date: 2008-10-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Pakos on 2008-10-08
I know that there are already a lot of scripts for saving power on a battery but i'm working on something a bit different so any help would be great ;)
Let me use numbers for questions, would be easier for you and me.

1. Deactivating hardware (for example usb via modprobe -r) would make less power usage?

2. Powertop: it's showing me some suggestions but everytime when i open it again i see there same suggestions. Isn't it forever? Or after each system reset i have to do it again?

3. If question nr 1 is true:
```
uvcvideo hci_usb rfcomm l2cap bluetooth usbhid uhci_hcd ehci_hcd sdhci mmc_core sr_mod cdrom
```
Removing these modules turns off cdrom, bluetooth, usb, camera and card reader (sd/mmc and so on ;d) right? Is it required to turn off some deamons, like bluetooth and anything else? 

4.Suggested from powertop:
```
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
hal-disable-polling --device /dev/cdrom
```
Second command works great, first one not.
Even when i use sudo it says "Permission denied", why?

5. Yet another suggestion from powertop:
```
Suggestion: increase the VM dirty writeback time from 0.30 to 15 seconds with:
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
```
I'm not sure what does it mean, should i use it?

6. Removing sound card. I can't figure it out, anyone could tell me which modules should be removed?

7. Suggestion form internet:
```
rmmod lp parport_pc ppdev parport 2> /dev/null;
echo "Parallel port is now OFF";;
```
What is a parallel port? ;p

8. Pcspkr module is for speakers? Or like in normal computers little speaker on motherboard?

9. Wifi - i'm using ndiswrapper for wifi so removing ndiswrapper module will turn off wifi?

10. Which module is used for lan card (where you put cable for the net ;d)

11. Should i turn off anything else? Or do you have any other ideas? ;)

Here is my lsmod:
```
lsmod 
Module                  Size  Used by
nls_cp437               8320  0 
isofs                  39464  0 
loop                   21508  0 
af_packet              27272  4 
ipv6                  311848  10 
i915                   38144  2 
drm                   105896  3 i915
binfmt_misc            14860  1 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
ppdev                  11400  0 
acpi_cpufreq           10832  2 
cpufreq_userspace       6180  0 
cpufreq_ondemand       11152  1 
cpufreq_stats           8416  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    10632  0 
cpufreq_powersave       3200  0 
container               6656  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
dock                   12960  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ndiswrapper           243872  0 
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
dcdbas                 11312  0 
uvcvideo               62084  0 
hci_usb                19228  2 
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
bluetooth              67748  7 rfcomm,l2cap,hci_usb
evdev                  14976  9 
snd_hda_intel         440408  4 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
video                  23444  0 
output                  5632  1 video
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
sdhci                  21508  0 
serio_raw               9092  0 
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ricoh_mmc               5120  0 
mmc_core               59272  1 sdhci
wmi_acer               11076  0 
battery                16776  0 
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 10912  0 
snd                    70856  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ac                      8328  0 
intel_agp              30624  1 
iTCO_wdt               15312  0 
iTCO_vendor_support     5764  1 iTCO_wdt
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
pcspkr                  4992  0 
soundcore              10400  1 snd
psmouse                46236  0 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
usbhid                 35296  0 
hid                    44992  1 usbhid
sg                     41880  0 
sd_mod                 33280  3 
ata_piix               24196  0 
ata_generic             9988  0 
ahci                   33028  2 
pata_acpi               9856  0 
ohci1394               36532  0 
libata                176432  4 ata_piix,ata_generic,ahci,pata_acpi
scsi_mod              178488  5 sbp2,sr_mod,sg,sd_mod,libata
ieee1394              106968  2 sbp2,ohci1394
tg3                   124804  0 
ehci_hcd               41996  0 
uhci_hcd               29856  0 
usbcore               169904  7 ndiswrapper,uvcvideo,hci_usb,usbhid,ehci_hcd,uhci_hcd
thermal                19744  0 
processor              41448  4 acpi_cpufreq,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 

```


Sorry for pretty lame questions but i'm trying to make bigger my linux knowledge ;)

---

### Post by iggykoopa on 2008-10-10
1. yes it will
2. it doesn't save the seettings you make
3. if you try to rmmod the modules it will tell you what other modules you have to stop first
4. you have to type in sudo su, that will give you a root terminal, then type in the command. For some reason you can't just run it with sudo.
5. it changes how often the journal is written back to the drive, it's relatively safe. But if you lose power any info you've done in those 30 seconds between write backs could be lost.
6. depends on what model of sound card you have
7. If you don't know what it is you should be safe to remove it, if your on a laptop you probably don't even have one. It used to be used for hooking up printers and the like.
8. the little speaker on the motherboard.
9. it should, I haven't tested it though because I have intel wireless. try removing it while running powertop and see if you save power.
10. I'd have to look it up again sorry forgot.
11. [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773) is a good thread about the subject. Also I'm working on a gui for the power management settings, it's going to be incorporated into wattos.

---

### Post by Pakos on 2008-10-13
3. I know that and with these modules everything works fine. I'm only wondering about deamons in /etc/init.d like bluetooth ;)

4. Thx but since it's working in script i will not do anything else :)

6. Lspci says: ```
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

7. Well yeah I'm on laptop so why these modules are used? 

11. I've seen that before but as I said I'm looking for some hardware which can be deactivated and everything from that post is used here ;)


Would be nice to get help with sound card as soon as possible. If anyone care about this here you can see my script, it's an early version so there can be something messed up so let me know if you see something :)
```
#!/bin/bash
# 
# Bash script for Dell XPS 1330
# Saves power by disconnecting some hardware
echo -e "Bash script for Dell XPS 1330\nSaves power by disconnecting some hardware\n";
echo -e "Choose option:\n1. Deactivate all.\n2. Activate all.\n";
read odp;
if [ $odp = 1 ]; then
echo "Deactivating all."
rmmod uvcvideo hci_usb rfcomm l2cap bluetooth usbhid uhci_hcd ehci_hcd sdhci mmc_core sr_mod cdrom 2> /dev/null
hal-disable-polling --device /dev/cdrom 1> /dev/null
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
echo min_power > /sys/class/scsi_host/host2/link_power_management_policy
elif [ $odp = 2 ]; then
echo "Activating all."
for MOD in uvcvideo hci_usb rfcomm l2cap bluetooth usbhid uhci_hcd ehci_hcd sdhci mmc_core sr_mod cdrom
do
modprobe $MOD 2> /dev/null
done
hal-disable-polling --enable-polling --device /dev/cdrom 1> /dev/null
echo 30 > /proc/sys/vm/dirty_writeback_centisecs
echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
echo max_performance > /sys/class/scsi_host/host1/link_power_management_policy
echo max_performance > /sys/class/scsi_host/host2/link_power_management_policy
else
echo "Something is wrong :)"
fi
exit 0

```

---

### Post by iggykoopa on 2008-10-13
for the sound /sys/module/snd_hda_intel/parameters/power_save is the file you wanna use and echo 10 to it for power saving and 0 for regular.

---

