---
title: "High load during drive read/write : need help understanding what they are"
date: 2006-06-25
forum: Desktop Environments
---

### Post by Bil-E-daKid on 2006-06-25
I'm experiencing the exact same problem as the guy here [http://www.ubuntuforums.org/showpost.php?p=1144745]("http://www.ubuntuforums.org/showpost.php?p=1144745")  and it seems to have started in the last few weeks since dapper was released (can't pin it down any more than that).

I have 2 x 160Gb SATA drives and, whenever anything starts using disk reads/writes - even an apt-get install <something>, the whole system bogs down, screen redraws take an age and mouse goes all jerky etc.

This is a P4 3Ghz machine running the 686 kernel with SMP extensions enabled and it has 2Gb DDR400 ram. It should not (and was not) doing this a little while ago.

I'd [obviously] really like to fix this and if anyone can tell me how to check drive performance/errors/bottlenecks etc or what to look for somewhere else, I would really appreciate it.

(output from hdparm -t -T)

/dev/sda:
Timing cached reads: 3912 MB in 2.00 seconds = 1955.88 MB/sec
Timing buffered disk reads: 106 MB in 3.19 seconds = 33.21 MB/sec

/dev/sdb:
Timing cached reads: 4008 MB in 2.00 seconds = 2003.87 MB/sec
Timing buffered disk reads: 72 MB in 3.00 seconds = 23.97 MB/sec

Regards
Bil-E-daKid

---

### Post by Shigun on 2006-06-26
While, this may not be related, I know that once when I had Gentoo, I had a similar issue due to a bad driver I had installed (was not the correct one for my card).  It may or may not help, dont know.  Hope you get it solved though.

---

### Post by Bil-E-daKid on 2006-06-26
Thanks Shigun - that's a good point.  Do you know how I might check which driver is being used?  Would I be correct in assuming it'd be a motherboard and/or SATA controller driver?  

Here's what's in /etc/modules:
lp
psmouse
sbp2
sr_mod

the output from lsmod:
Module                  Size  Used by
vmnet                  40036  7 
vmmon                 117644  12 
isofs                  38496  0 
udf                    94628  0 
nls_utf8                2240  0 
nls_cp437               5888  0 
vfat                   14496  0 
fat                    55548  1 vfat
usb_storage            79488  0 
ipaq                   32760  0 
usbserial              33224  1 ipaq
i915                   21664  0 
drm                    78484  1 i915
ppdev                   9668  0 
video                  16324  0 
tc1100_wmi              6884  0 
sony_acpi               5580  0 
pcc_acpi               12416  0 
hotkey                 11492  0 
dev_acpi               11236  0 
container               4608  0 
button                  6704  0 
acpi_sbs               20172  0 
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               22848  1 i2c_acpi_ec
af_packet              24520  2 
ext2                   74152  1 
dm_mod                 63256  1 
sr_mod                 17988  0 
sbp2                   25060  0 
lp                     12356  0 
tsdev                   8032  0 
floppy                 64676  0 
parport_pc             37988  1 
parport                39400  3 ppdev,lp,parport_pc
usbhid                 42752  0 
pcspkr                  2244  0 
psmouse                40004  0 
e1000                 124440  0 
serio_raw               7748  0 
snd_hda_intel          20468  3 
snd_hda_codec         151056  1 snd_hda_intel
snd_pcm_oss            56448  0 
snd_mixer_oss          20544  2 snd_pcm_oss
snd_pcm                96708  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  2 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm
hw_random               5716  0 
shpchp                 49504  0 
pci_hotplug            30788  1 shpchp
intel_agp              24700  1 
agpgart                36784  2 drm,intel_agp
sg                     40160  0 
evdev                  10176  2 
ipv6                  286976  31 
ext3                  148104  3 
jbd                    65876  1 ext3
ide_generic             1504  0 
ohci1394               37524  0 
ieee1394              306520  2 sbp2,ohci1394
ehci_hcd               36104  0 
uhci_hcd               35408  0 
usbcore               139076  7 usb_storage,ipaq,usbserial,usbhid,ehci_hcd,uhci_hcd
sd_mod                 20448  7 
ata_piix               11364  10 
libata                 83440  1 ata_piix
scsi_mod              145960  6 usb_storage,sr_mod,sbp2,sg,sd_mod,libata
ide_cd                 35780  0 
cdrom                  41408  2 sr_mod,ide_cd
piix                   11652  1 
generic                 5124  0 
thermal                13768  0 
processor              26344  1 thermal
fan                     4836  0 
capability              4968  0 
commoncap               7328  1 capability
vesafb                  8636  1 
fbcon                  43904  77 
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

---

### Post by scxtt on 2006-06-26
[QUOTE=Bil-E-daKid](output from hdparm -t -T)

/dev/sda:
Timing buffered disk reads: 106 MB in 3.19 seconds = 33.21 MB/sec

/dev/sdb:
Timing buffered disk reads: 72 MB in 3.00 seconds = 23.97 MB/sec[/QUOTE]these #'s seem *awfully* low for SATA drives, i'm getting ~75 MB/sec ... maybe there's a problem w/ the driver ... i was getting #'s like that w/ IDE drives ...

---

### Post by Bil-E-daKid on 2006-06-26
Yeah - that's what I thought.  Unfortunately, I don't have any hdparm stats from before the problem occured to compare these with.

Do you know how I'd check what driver is being used and possibly change/reconfigure it?

---

### Post by Bil-E-daKid on 2006-06-27
Well, just did my first install from the new LiveCD installer and am currently readding all the extra apps I need.

Very impressed with the speed of the whole process - niiiice!  And I could keep working as we use Terminal Server here at work which was even kewler!

Here's my hdparm stats now:
/dev/sda:
 Timing cached reads:   4616 MB in  2.00 seconds = 2307.20 MB/sec
 Timing buffered disk reads:  206 MB in  3.02 seconds =  68.20 MB/sec

/dev/sdb:
 Timing cached reads:   4524 MB in  2.00 seconds = 2262.34 MB/sec
 Timing buffered disk reads:  214 MB in  3.00 seconds =  71.25 MB/sec

Much better!  :-)

---

### Post by Bil-E-daKid on 2006-06-27
[QUOTE=Bil-E-daKid]
Much better!  :-)[/QUOTE]

Oops - spoke to soon.  Just installed latest VMWare Server beta (used to run XP workstation and Windows 2003 Server) - here's the stats:

/dev/sdb:
 Timing cached reads:   4068 MB in  2.00 seconds = 2033.87 MB/sec
 Timing buffered disk reads:   90 MB in  3.08 seconds =  29.26 MB/sec

/dev/sda:
 Timing cached reads:   3924 MB in  2.00 seconds = 1961.88 MB/sec
 Timing buffered disk reads:   92 MB in  3.13 seconds =  29.37 MB/sec

That's with the VM's running but not doing anything intensive - sitting fairly idle. With them off completely, the stats become:

/dev/sda:
 Timing cached reads:   4200 MB in  2.00 seconds = 2099.87 MB/sec
 Timing buffered disk reads:  202 MB in  3.02 seconds =  66.88 MB/sec

/dev/sdb:
 Timing cached reads:   4100 MB in  2.00 seconds = 2049.87 MB/sec
 Timing buffered disk reads:  214 MB in  3.01 seconds =  71.04 MB/sec

So, there's the problem then - it's something to do with VMware server - but only started happening recently.  Thanks everyone who helped - I'm off to the Server Beta forums now - bye!

---

