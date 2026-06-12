---
title: "Kino Problem"
date: 2005-10-30
forum: Desktop Environments
---

### Post by G Sizzle on 2005-10-30
I've looked around for a solution to this kino problem, and im sure its just waiting to jump at me but my sleep deprivation is keeping me from finding it.  I've installed Kino using Snaptic and my camcoder is connected via firewire 1394 4 pin conectors.  Under preferences in Kino it reads "The IEEE 1394 Subsystem is not responding.  The raw1394 module must be loaded, and you must have read and write access to /dev/raw1394"  How must I solve this problem I have a video that desperately needs to be edited.  My English grade depends on your help.  Thanks.

---

### Post by claydoh on 2005-10-30
You can try running kino as root, you can use the steps listed [here]("http://ubuntuforums.org/showthread.php?t=56468&highlight=raw1394")
but I just discovered that if I add my login to the "disk" group I can access the camera as user. I do not know what the implications of the "disk" group entail, but it works :) as did the second method.

---

### Post by G Sizzle on 2005-10-31
Now I'm getting an error when i go to the capture screen which says "Warning Raw1394 kernel module not loaded or failure to read/write dev/..."  Thanks for your help so far.

---

### Post by GeneralZod on 2005-10-31
Can you post the output of 

```

lsmod

```
?

---

### Post by G Sizzle on 2005-10-31
guy@gsizzle:~$ lsmod
Module                  Size  Used by
ipv6                  217408  6
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_ich           5132  0
speedstep_lib           4228  1 speedstep_ich
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_ich,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  4
radeon                 68352  1
drm                    58004  2 radeon
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
af_packet              20232  4
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
ath_pci                69148  0
ath_rate_sample        14344  1 ath_pci
wlan                  120988  3 ath_pci,ath_rate_sample
ath_hal               148432  3 ath_pci,ath_rate_sample
ohci1394               30644  0
yenta_socket           22540  3
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           30144  3
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  2 drm,intel_agp
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
sr_mod                 15652  0
sbp2                   21128  0
scsi_mod              124872  2 sr_mod,sbp2
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
3c59x                  37544  0
mii                     5248  1 3c59x
uhci_hcd               28048  0
usbcore               104188  2 uhci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  668
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

### Post by chele on 2005-11-11
Try a 'sudo modprobe video1394'

Then a 'lsmod | grep 1394' and paste the output here.

---

### Post by Rev. Nathan on 2005-11-11
I too am having this problem. I am the root user? This is the one and only log in name, the one I assigned when I install ubuntu.
[QUOTE=chele]Try a 'sudo modprobe video1394'

Then a 'lsmod | grep 1394' and paste the output here.[/QUOTE]
nathan@main:~$ lsmod | grep 1394
video1394              18380  0
dv1394                 18764  0
raw1394                26348  0
ohci1394               30644  2 video1394,dv1394
ieee1394               90936  5 video1394,dv1394,raw1394,ohci1394,sbp2

Is what I get.

Thank you in advance you guys; I'm trying to fully make the move to Linux, and this one of the last things.

To specify, in the tutorial ClayDoh posted in the other thread, when I open /etc/modules in terminal (by typing 'gedit /etc/modules'), it is a read-only file; I cannot modify it!

---

### Post by chele on 2005-11-11
It is working here now for me as my normal user. Don't bother with being root, that is just for troubleshooting permissions.  Run 'ls -al /dev/raw1394'

chele@brick:~$ ls -al /dev/raw1394

crw-rw----   1 root disk    171,   0 2005-11-07 19:10 raw1394


The key seems to be having membership in the 'disk' group and the group permissions being 'rw'. This device was in the video group before, it seems to have moved to the disk group with the upgrade to breezy.

---

### Post by TacyTurn on 2005-11-12
I found how to put back /dev/raw1394 in the "video" group. I am very new to Ubuntu so I am not quite sure it was a smart thing to do - the developpers probably had a good reason to set the group to "disk" - but the following worked for me and after that simple change any user in the "video" group can now use ieee1394 under kino.

Simply edit the /etc/udev/permissions.rules file (as root or using "sudo" and making a backup copy...) and replace the "disk" group by "video" as follows:

#KERNEL=="raw1394",      GROUP="disk"
KERNEL=="raw1394",      GROUP="video"

After rebooting ls -l /dev/raw1394 returns:
crw-rw----  1 root **video **171, 0 2005-11-12 21:12 /dev/raw1394

---

