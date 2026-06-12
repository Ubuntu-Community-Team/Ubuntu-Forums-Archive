---
title: "No sound (after playing around with microphone?)"
date: 2010-08-11
forum: Desktop Environments
---

### Post by Matthes on 2010-08-11
I use a ThinkPad T60 with Ubuntu 10.4, kernel 2.6.32.24-generic (x86_64) and a HDA-Intel sound card (I hope I got the right information here.)

The day before I tried to get a microphone running, but didn't really succeed. Then I hibernated, suspended or rebooted and now I can't get any more sound out of the build-in speakers as well as of headphones plugged in.

I already tried killing pulseaudio, changing settings in alsamixer and the pulseaudio Mixer, muting and unmuting my system, but nothing helped.

I also asked on #ubuntu, but I didn't get much help there. :(

That's the reason why I ask here now. :) Ideas how to make my system noisy again?

Edit: I also made a post here: [http://ubuntuforums.org/showthread.php?p=9710745#post9710745](http://ubuntuforums.org/showthread.php?p=9710745#post9710745) 
 


I also added &quot;options snd-hda-intel model=thinkpad&quot; to /etc/modprobe.d/alsa-base.conf according to [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) but it made my system unbootable and I had to revert the change via a live usb-stick. :/ 
 
On the stick I could play music (at least I heard the Ubuntu startup sound) so it can't be a hardware defect.  
 
 Edit2:  lspci 
 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02) 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) 00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) 00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) 00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02) 00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02) 00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) 00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) 00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) 00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) 00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02) 01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300] 02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller 03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) 15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

---

### Post by Matthes on 2010-08-13
lsmod 
Module                  Size  Used by
cryptd                  8116  0 
aes_x86_64              7912  2 
aes_generic            27607  1 aes_x86_64
binfmt_misc             7960  1 
ppdev                   6375  0 
hdaps                  10772  1 
thinkpad_ec             5842  1 hdaps
rfcomm                 40393  0 
sco                     9617  0 
bridge                 53184  0 
stp                     2171  1 bridge
bnep                   11884  0 
l2cap                  34806  4 rfcomm,bnep
btusb                  12969  0 
bluetooth              58685  5 rfcomm,sco,bnep,l2cap,btusb
joydev                 11072  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_codec_analog    78702  1 
pcmcia                 35580  0 
snd_hda_intel          25677  0 
snd_hda_codec          85759  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1473  2 
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwl3945                79436  0 
radeon                740390  2 
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               124955  1 iwl3945
dvb_usb_af9015         30239  0 
ttm                    60847  1 radeon
yenta_socket           22901  1 
rsrc_nonstatic          9830  1 yenta_socket
nsc_ircc               21412  0 
dvb_usb                16709  1 dvb_usb_af9015
mac80211              238448  2 iwl3945,iwlcore
psmouse                64576  0 
drm_kms_helper         30742  1 radeon
video                  20623  0 
output                  2503  1 video
thinkpad_acpi          79367  0 
led_class               3764  3 iwl3945,iwlcore,thinkpad_acpi
nvram                   7639  1 thinkpad_acpi
tpm_tis                 9742  0 
tpm                    15780  1 tpm_tis
tpm_bios                6402  1 tpm
irda                  205699  1 nsc_ircc
crc_ccitt               1675  1 irda
dvb_core              102993  1 dvb_usb
snd                    71106  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
pcmcia_core            38176  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               4918  0 
intel_agp              29095  0 
cfg80211              148546  3 iwl3945,iwlcore,mac80211
drm                   199204  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            6024  1 radeon
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   37870  4 
e1000e                136205  0

---

### Post by Matthes on 2010-08-13
I think the problem is that I created a loop directly connecting the sound output with the mic input without any hardware speaker being in between. How can I fix it?

---

### Post by Matthes on 2010-08-14
I created another user and I had sound there.

I deleted some local configuration files and now I have sound again. :)

---

