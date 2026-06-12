---
title: "Cannot &quot;See&quot; the media in CDROM from within Nautalis"
date: 2007-10-01
forum: Dell  Ubuntu Support
---

### Post by paul@cyberengel.com on 2007-10-01
I've just gotten two (2) Dell Optiplex GX150s and put Feisty Faun (7.04) and let it update.

When I put a CD (audio or data) in the CD it doesn't automount.  If I double-click the CDrom icon in Nautalis it says it cannot mount and there may not be any media in the drive even with the disc I used to build the system.  I can however mount a disc from the command line using "sudo mount /media/cdrom0"

---

### Post by logos34 on 2007-10-01
system>prefs>removable drives and media>starge tab>"mount reovable media when inserted" (x)

multimedia tab>"play audio cds when inserted" (x)

Post you fstab:
[B]
cat /etc/fstab[/B]

---

### Post by paul@cyberengel.com on 2007-10-02
Both "mount removable media when inserted" and "play audio cds when inserted" are checked.

**fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4f826724-2208-49ae-8f9b-9b4428b7ac9d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b01da8d4-013e-4fc3-891a-aee2642114dd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by nowshining on 2007-10-03
what is the output of lsmod in terminal.

---

### Post by paul@cyberengel.com on 2007-10-03
Module                  Size  Used by
udf                    85252  0
nls_cp437               6784  0
isofs                  36284  0
binfmt_misc            12680  1
rfcomm                 40856  0
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0
speedstep_lib           6148  0
cpufreq_ondemand        9228  0
cpufreq_conservative     8200  0
cpufreq_stats           7360  0
cpufreq_userspace       5408  0
cpufreq_powersave       2688  0
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
sony_acpi               6284  0
tc1100_wmi              8068  0
dev_acpi               12292  0
pcc_acpi               13184  0
battery                10756  0
ac                      6020  0
container               5248  0
asus_acpi              17308  0
video                  16388  0
sbs                    15652  0
i2c_ec                  6016  1 sbs
button                  8720  0
dock                   10268  0
backlight               7040  1 asus_acpi
ipv6                  268960  14
lp                     12452  0
fuse                   46612  0
snd_intel8x0           34332  1
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               7940  0
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
pcspkr                  4224  0
psmouse                38920  0
i2c_i810                6276  0
i2c_algo_bit            8712  1 i2c_i810
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
intel_agp              26140  1
agpgart                35400  2 intel_agp
i2c_core               22656  3 i2c_ec,i2c_i810,i2c_algo_bit
iTCO_wdt               11812  0
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
af_packet              23816  2
tsdev                   8768  0
evdev                  11008  3
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0
sr_mod                 17060  0
cdrom                  37664  1 sr_mod
sd_mod                 23428  3
floppy                 59524  0
3c59x                  46632  0
mii                     6528  1 3c59x
uhci_hcd               25360  0
usbcore               134280  2 uhci_hcd
ata_piix               15492  2
ata_generic             9092  0
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
generic                 5124  0 [permanent]
thermal                14856  0
processor              31048  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability

---

### Post by nowshining on 2007-10-04
lsmod looks fine to me, the module to read/load cds are there.

open up a terinal and type

gconf-editor

hi enter and navigate to

/desktop/gnome/volume_manager

Make sure:
automount_drives

&

automount_media

are both checked - no need to reboot - it should already be ready - try again - if not, reboot and try again, if not report back ur results.

---

### Post by paul@cyberengel.com on 2007-10-04
Both automount_drivers and automount_media were checked already.

---

### Post by nowshining on 2007-10-04
okay have you messed with blacklisting modules lately?

---

### Post by paul@cyberengel.com on 2007-10-05
Nope... all I did was install it, let it update, added some packages for audio/video, (Ubuntu Studio) and then tried to play/rip a CD.  That's when I noticed the problem.

The interesting thing is I have a laptop also running Feisty and when I put a DVD in the drive it works fine.  It's only these two Dell boxes.  I've tried multiple CDs to make sure it wasn't a problem with one of them.

---

