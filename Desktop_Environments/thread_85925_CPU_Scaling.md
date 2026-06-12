---
title: "CPU Scaling"
date: 2005-11-03
forum: Desktop Environments
---

### Post by chubsmalone on 2005-11-03
I've been searching for hours trying to get this to work, including posts in these forums...I just keep getting more and more confused.  I hope somebody can help me get this going...

I am running breezy on a dell inspiron 1200 laptop computer.  Nearly everything worked out of the box, but I want to have some control over the frequency scaling so I can conserve some battery when necessary.  

I think I have all of the appropriate software to make this work.  When I add the CPU frequency scaling monitor applet for gnome, I get an error that says:

You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

I know that my processor (Celeron M 1300) supports frequency throttling because I was running debian and it would always say so in the start up stuff.  

I assume the problem is misconfiguration, but I do not know what to configure.  Please help.

---

### Post by chubsmalone on 2005-11-03
I looked around to see what information may be useful to help me figure this out...
Here is the output of ~#lsmod
~#lsmod
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
i915                   17920  1
drm                    58004  2 i915
ipv6                  217408  12
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
af_packet              20232  2
pcspkr                  3652  0
rtc                    11832  0
yenta_socket           22540  2
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
snd_intel8x0           30144  0
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
intel_agp              21276  1
agpgart                32328  3 drm,intel_agp
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
ndiswrapper           144596  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
e100                   32768  0
mii                     5248  1 e100
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  4 ndiswrapper,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  732
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

---

