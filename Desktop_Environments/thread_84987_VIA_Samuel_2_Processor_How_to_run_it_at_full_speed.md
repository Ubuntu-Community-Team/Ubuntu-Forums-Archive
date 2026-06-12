---
title: "VIA Samuel 2 Processor: How to run it at full speed?"
date: 2005-11-01
forum: Desktop Environments
---

### Post by istoyanov on 2005-11-01
Since I installed Ubuntu 5.10 I was really disappointed by the performance of my box, but recently I noticed accidentally (via cat /proc/cpuinfo) that the CPU runs only at *half* the speed that it is supposed to run. I assume this is somehow regulated by one (or more) of the really numerously (compared to previous versions of Ubuntu) loaded drivers, but have no idea *what* and *how* to disable.

My question is: how to bring the CPU to its full speed?

Any hints would be much appreciated:) 

FYI: The output of lsmod follows.
```

Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
longhaul                7760  0
cpufreq_powersave       1920  0
cpufreq_stats           5124  0
cpufreq_userspace       4444  1
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
freq_table              4484  2 longhaul,cpufreq_stats
tc1100_wmi              6916  0
video                  16004  0
battery                 9604  0
container               4608  0
i2c_acpi_ec             5760  0
button                  6672  0
pcc_acpi               11392  0
sony_acpi               5516  0
ac                      4996  0
dev_acpi               11396  0
hotkey                  9508  0
ipv6                  217408  6
af_packet              20232  2
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  1
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
via686a                17816  0
i2c_sensor              3456  1 via686a
i2c_viapro              7696  0
i2c_core               19728  4 i2c_acpi_ec,via686a,i2c_sensor,i2c_viapro
pci_hotplug            24628  0
via_agp                 9472  1
agpgart                32328  1 via_agp
ext3                  115976  1
jbd                    48536  1 ext3
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
reiserfs              217200  2
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
8139cp                 18432  0
8139too                23552  0
mii                     5248  2 8139cp,8139too
uhci_hcd               28048  0
usbcore               104188  2 uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  5
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  611
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```

---

### Post by domthom on 2006-04-19
I noticed accidentally (via cat /proc/cpuinfo) the same problem on my comp.

processor       : 0
vendor_id       : CentaurHauls
cpu family      : 6
model           : 7
model name      : VIA Samuel 2
stepping        : 1
cpu MHz         : 300.612  <-- (should be at 700!)

I thought my machine is generally crap.](*,)
Will check my BIOS settings. Stay on.

---

### Post by domthom on 2006-04-19
got the solution here: [http://ubuntuforums.org/showthread.php?p=938137#post938137]("http://ubuntuforums.org/showthread.php?p=938137#post938137")

Adding the following to /etc/modprobe.d/aliases did the trick:

alias longhaul off

mfg domthom.

---

### Post by TuxCrafter on 2006-07-19
I am building a how to how to run your Via epia with a faster cpu frequentie.
I have a Epia ME6000 and it runs very stable on 733 MHz i can get 800 for example.

---

