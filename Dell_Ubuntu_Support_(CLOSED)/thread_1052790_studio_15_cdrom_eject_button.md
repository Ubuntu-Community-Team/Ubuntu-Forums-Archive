---
title: "studio 15 cdrom eject button"
date: 2009-01-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by computx on 2009-01-28
I recently purchased a refurbed studio 15 from the dell outlet. I installed ubuntu and hardware support has been excellent except for 1 problem. The eject key doesn't eject the cdrom. all the other multimedia keys seem to be working fine. I also tried fn + f10 but that too doesnt eject the cdrom. I temporarily assigned shift f10 to this functionality and that does work but does anyone know if there are drivers required to use the mm eject key to work properly? Google hasn't turned anything up for me. 
  Otherwise I am very happy with this studio 15's ubuntu support.

---

### Post by danhm on 2009-01-28
I just got a new Studio 15 today and was wondering the same thing! It appears to be setup correctly in the "Keyboard Shortcuts" program.

---

### Post by Xica_da_Silva on 2009-01-28
I had this problem, too...this worked for me as a work-around at least(albeit a bit inconvenient):

Go to Applications menu -> Accessories -> Terminal and then type in:

sudo eject 

Hit 'enter'. 

But I'm not sure how to fix the underlying issue causing this(fairly new myself, sorry).

---

### Post by computx on 2009-01-28
Yes I knew about the eject command and I was able to assign it to shift F10 as I stated above but was hoping there was a way to make the eject key work properly.

---

### Post by conorsulli on 2009-01-31
OK i have fixed this on 2 dell studios, simply.. in the terminal:
sudo gedit /etc/sysctl.conf
then at the bottom of the opened text add:

# Unlock the CDROM eject button
dev.cdrom.lock=0

Then save it....

reboot your computer and It should work. hope this helps.

---

### Post by rklk on 2009-01-31
with dev.cdrom.lock set to 0 eject button ejects the cd indeed. but it does not unmount it beforehand, it leaves the cd icon on the desktop and cd content in nautilus is still present

btw i have dell xps m1330

---

### Post by computx on 2009-01-31
Yes the sysctl hack is only half a solution as far as I am concerned. I am curious if anyone with a studio 15 that Dell preinstalled with ubuntu has this problem.

---

### Post by bloodofangels302 on 2009-02-03
I have a studio 15 that was pre installed by dell with 8.04 and I don't have this problem.  Unfortunately though none of the other media controls work.  I am still new to ubuntu so if there is anything I can check for on my machine to help you solve your problem please let me know.

---

### Post by superm1 on 2009-02-03
> **bloodofangels302 said:**
> I have a studio 15 that was pre installed by dell with 8.04 and I don't have this problem.  Unfortunately though none of the other media controls work.  I am still new to ubuntu so if there is anything I can check for on my machine to help you solve your problem please let me know.
All of the media buttons should be working on the studio 15.  They only work however in applications that normally can use them.  Try opening Rhythmbox, and you'll see them in action therer.

---

### Post by computx on 2009-02-04
>  I am still new to ubuntu so if there is anything I can check for on my machine to help you solve your problem please let me know. 
Thanks, could you open a terminal and type lsmod and post the results? lsmod should list which drivers you are using and I can compare it to the drivers I am using on my studio 15.

---

### Post by bloodofangels302 on 2009-02-04
> **computx said:**
> Thanks, could you open a terminal and type lsmod and post the results? lsmod should list which drivers you are using and I can compare it to the drivers I am using on my studio 15.

sure, here u go hope it helps

Module                  Size  Used by
af_packet              23812  4 
ipv6                  267908  10 
i915                   32512  2 
drm                    82452  3 i915
hci_usb                16540  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61028  7 hci_usb,rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_powersave       2688  0 
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
snd_hda_intel         355364  3 
dcdbas                  9504  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
serio_raw               7940  0 
uvcvideo               60936  0 
pcspkr                  4224  0 
psmouse                40336  0 
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
v4l2_common            18304  2 uvcvideo,videodev
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
sdhci                  19076  0 
ricoh_mmc               4352  0 
mmc_core               51460  1 sdhci
evdev                  13056  10 
snd_seq_midi            9376  0 
iTCO_wdt               13092  0 
snd_rawmidi            25760  1 snd_seq_midi
iTCO_vendor_support     4868  1 iTCO_wdt
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
ieee80211_crypt_tkip    11648  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
wl                   1077908  0 
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,wl
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  19856  0 
output                  4736  1 video
wmi_acer                9644  0 
intel_agp              25492  1 
button                  9232  0 
battery                14212  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
ac                      6916  0 
agpgart                34760  3 drm,intel_agp
soundcore               8800  1 snd
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
usbhid                 32128  0 
hid                    38784  1 usbhid
ahci                   28548  2 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
libata                159600  1 ahci
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
tg3                   116228  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  6 hci_usb,uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36488  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

---

