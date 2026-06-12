---
title: "Random Xorg Freezes - Dell OptiPlex GX280"
date: 2006-09-12
forum: Desktop Environments
---

### Post by flickerfly on 2006-09-12
For the last month, I am experiencing random freezing of Xorg. I'm running a Dell Optiplex GX280. I've been slowly watching this and trying to debug it. 

**My Symptoms:**
I return from being away from my desk and log into X (screensaver password protecte). I almost always have a grdesktop session opened into a Win2k3 terminal server for Outlook. I enter my password into that if the screensaver is up or simply move the mouse over it. The screen pauses unusually long then shows the grdesktop. I can't click on anything or interact with the desktop. Moving to an open terminal window not on the term server, I can't select the window or type in it. I can't select other virtual desktops or select the menu items in the upper-left. I can't click on anything, but my mouse moves around fine. The keyboard works only inside the password dialog boxes.

I typically have firefox open and a number of Terminal windows in addition to the grdesktop session or three.

Oddly, it never seems to happen when I am actually using the machine, though it may happen if I've been away for only a minute answering a question of someone who walks into my office.

I have gone as many as three days without a freeze, but I've seen as many as 4 freezes in a day with gaps as short as an hour between them. The gaps do not coorelate with the amount of usage the machine is experiencing during the gap.

I have eliminated grdesktop, firefox and the terminal windows and seen the freeze. (I think, there's room for error in that last statement but I'm confident enough to say it.)

**My "Fix":**
This problem is resovled by Ctrl-Alt-F1 to a virt term and entering the command 'sudo /etc/init.d/gdm restart'. This, of course, is a bit annoying as I lose what I'm working on.

**My Question:**
I'm starting to wonder if it could be related to the use of GL in screensavers, but I have no basis for this. Are there any other ideas what might be causing it or things that I could use to debug this mess?

**My Hardware & Config:**
```
$ lspci
0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00c3 (rev a2)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
0000:04:02.0 Ethernet controller: 3Com Corporation 3c900 10BaseT [Boomerang]
```

```
$ uname -a
Linux jritchie 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686 GNU/Linux
```

```
$ lsmod
Module                  Size  Used by
nls_cp437               5888  0
isofs                  38496  0
udf                    94628  0
binfmt_misc            13064  1
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54084  4 rfcomm,l2cap
ppdev                   9668  0
speedstep_lib           4580  0
cpufreq_userspace       6496  0
cpufreq_stats           6688  0
freq_table              4928  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
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
ipv6                  286976  24
af_packet              24520  6
8021q                  22664  0
dm_mod                 63256  1
md_mod                 76052  0
lp                     12356  0
tsdev                   8032  0
psmouse                40004  0
serio_raw               7748  0
floppy                 64676  0
parport_pc             37988  1
parport                39400  3 ppdev,lp,parport_pc
pcspkr                  2244  0
3c59x                  47784  0
mii                     6176  1 3c59x
usbhid                 42752  0
snd_intel8x0           35772  1
snd_ac97_codec        100224  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
nvidia               4552660  12
snd                    60004  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
tg3                   113060  0
soundcore              10784  1 snd
hw_random               5716  0
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm
i2c_core               22848  2 i2c_acpi_ec,nvidia
intel_agp              24700  1
agpgart                36784  2 nvidia,intel_agp
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
sg                     40160  0
evdev                  10176  1
ext3                  148104  1
jbd                    65876  1 ext3
ide_generic             1504  0
uhci_hcd               35408  0
ehci_hcd               36104  0
usbcore               139076  4 usbhid,uhci_hcd,ehci_hcd
sd_mod                 20448  3
ata_piix               11364  4
libata                 83440  1 ata_piix
scsi_mod              145960  3 sg,sd_mod,libata
ide_cd                 35780  0
cdrom                  41408  1 ide_cd
piix                   11652  1
generic                 5124  0
thermal                13768  0
processor              26888  1 thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

```

---

### Post by flickerfly on 2006-09-12
I should have mentioned that this is a dual-head setup and that there are no warning or error lines in my Xorg log file, except for something saying a font directory doesn't exist that I'm not worried about. I didn't find anything related in other logs.

---

### Post by awclemen on 2008-06-25
I hate to bring this issue back up from the depths, but I am currently experiencing the same problem.

I'm getting Xorg freezes randomly, however it is slightly different than the above user in the fact that I am always currently using the system when the freeze occurs.  Hopefully someone has a work-around or solution?

Anyway, here's some machine info:
```

bmiller@bug-a-boo:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

```

```
bmiller@bug-a-boo:~$ uname -a
Linux bug-a-boo 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

```

```
bmiller@bug-a-boo:~$ lsmod
Module                  Size  Used by
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
video                  19856  0 
output                  4736  1 video
container               5632  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
dcdbas                  9504  0 
snd_rawmidi            25760  1 snd_seq_midi
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
psmouse                40336  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
serio_raw               7940  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ipv6                  267780  8 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4224  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
evdev                  13056  4 
button                  9232  0 
intel_agp              25492  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 drm,intel_agp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sd_mod                 30720  3 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
pata_acpi               8320  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
ata_piix               19588  2 
libata                159344  3 ata_generic,pata_acpi,ata_piix
scsi_mod              151436  4 sg,sd_mod,sr_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  4 usbhid,ehci_hcd,uhci_hcd
tg3                   116228  0 
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```

Is there a place to submit bugs?  Maybe I should go there?

Thanks for the help!

--Andy

---

