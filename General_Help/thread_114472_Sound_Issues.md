---
title: "Sound Issues"
date: 2006-01-08
forum: General Help
---

### Post by starfleetcaptainrob on 2006-01-08
Hi there, I'm still pretty new at linux, but I'm learning.  Anyhow, I'm hoping someone can help me.  For whatever reason my sound has decided to stop working.  It worked fine for the longest time and now all of the sudden it doesn't work.  I haven't changed anything or upgraded anything or downloaded any new programs.  I have a Creative Sound Blaster Live 5.1 card.  I've checked all the wires and nothing is unplugged or chewed on by our cats, the card is seated correctly in the mobo, I checked ALSA mixer and everything is turned on all the way up and un muted and I've tried atleast half a dozen suggestions for similar problems posted on the forums here.  I'm just baffled.  If someone can help it would be greatly appreciated!  I can post whatever info you need, just tell me where I should be able to find it.  

Thanks in advance!

---

### Post by TikkiRo on 2006-01-08
[COLOR="Purple"]Hmm - I've had that problem quite a few times myself too and also now find sometimes while I have sound it's at half volume which is frustrating too.  For me at least, it appears to be happening (with Amarok in particular) after I've used another media player.  Like you tho initially I found it happened straight off after booting up, but I found a reboot or reset of the linux environment did the trick and 'released' it - to my (limited) knowledge I did see something somewhere about this being related to particular soundcards, with SB being one of them I think.  If you do a search on the forums for sound issues you might be able to track whether others have had the same problem - about to go and do that myself first before seeking more help too on my low volume problem.  Hope you find a better solution soon tho.[/COLOR]

Whoops - sorry just reread your post - see you've already tried that one :(.  Maybe try a different search query tho?  The search facility in this forum isn't really the most specific at times!

---

### Post by pauljwells on 2006-01-08
I had a problem where my sound stopped working too. I finally traced it to RealPlayer. You have to open any realplayer file and set the volume to maximum, then it all works again. Your mileage may vary, of course.

---

### Post by starfleetcaptainrob on 2006-01-08
Here's my lsmod
```
Module                  Size  Used by
rfcomm                 38748  0
l2cap                  25156  5 rfcomm
bluetooth              48580  4 rfcomm,l2cap
cpufreq_userspace       4380  0
cpufreq_stats           5316  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1792  0
cpufreq_ondemand        6108  0
cpufreq_conservative     7012  0
video                  15812  0
tc1100_wmi              6788  0
sony_acpi               5388  0
pcc_acpi               11200  0
hotkey                  9380  0
dev_acpi               11268  0
i2c_acpi_ec             5568  0
button                  6544  0
battery                 9412  0
container               4480  0
ac                      4804  0
ipv6                  252544  6
af_packet              22088  2
analog                 11680  0
snd_mpu401              6408  0
snd_mpu401_uart         7360  1 snd_mpu401
floppy                 59412  0
pcspkr                  3460  0
rtc                    12408  0
usblp                  12736  0
snd_usb_audio          75712  0
snd_usb_lib            15680  1 snd_usb_audio
pwc                    88756  0
videodev                9536  1 pwc
v4l2_common             5824  1 pwc
emu10k1_gp              3712  0
gameport               14920  3 analog,emu10k1_gp
snd_emu10k1_synth       7616  0
snd_emux_synth         36096  1 snd_emu10k1_synth
snd_seq_virmidi         7232  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           118404  2 snd_emu10k1_synth
snd_ac97_codec         84028  1 snd_emu10k1
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  4 snd_usb_audio,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10696  2 snd_emu10k1,snd_pcm
snd_util_mem            4544  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8992  3 snd_usb_audio,snd_emux_synth,snd_emu10k1
shpchp                 97252  0
pci_hotplug            27636  1 shpchp
i2c_nforce2             6784  0
i2c_core               21328  2 i2c_acpi_ec,i2c_nforce2
amd64_agp              12296  0
nls_iso8859_1           4096  3
vfat                   13696  3
fat                    53020  1 vfat
nls_cp437               5760  4
ntfs                  109104  1
dm_mod                 58044  1
tsdev                   7872  0
nvidia               3711172  12
agpgart                34888  2 amd64_agp,nvidia
snd_seq_dummy           3716  0
snd_seq_oss            33664  0
snd_seq_midi            9184  0
snd_rawmidi            25056  5 snd_mpu401_uart,snd_usb_lib,snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      7040  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51024  10 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24260  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          8524  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
evdev                   9728  0
snd                    55172  19 snd_mpu401,snd_mpu401_uart,snd_usb_audio,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9696  1 snd
psmouse                30212  0
mousedev               11680  1
parport_pc             35460  1
lp                     12420  0
parport                36104  2 parport_pc,lp
sd_mod                 19216  2
md                     45648  0
ext3                  137352  1
jbd                    55128  1 ext3
mbcache                 9348  1 ext3
thermal                13064  0
processor              22908  1 thermal
fan                     4548  0
usb_storage            74560  2
forcedeth              21568  0
ehci_hcd               34312  0
ohci_hcd               20740  0
usbcore               118396  8 usblp,snd_usb_audio,snd_usb_lib,pwc,usb_storage,ehci_hcd,ohci_hcd
ide_cd                 41732  0
cdrom                  39904  1 ide_cd
ide_disk               18560  7
ide_generic             1472  0
sata_nv                 9412  0
libata                 54020  1 sata_nv
scsi_mod              135944  3 sd_mod,usb_storage,libata
amd74xx                14044  1
ide_core              139028  5 usb_storage,ide_cd,ide_disk,ide_generic,amd74xx
unix                   27248  572
vesafb                  8088  0
capability              4808  0
commoncap               6912  1 capability
vga16fb                12680  1
vgastate                9792  1 vga16fb
softcursor              2496  2 vesafb,vga16fb
cfbimgblt               3008  2 vesafb,vga16fb
cfbfillrect             3968  2 vesafb,vga16fb
cfbcopyarea             4672  2 vesafb,vga16fb
fbcon                  39104  72
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 5696  1 fbcon

```
and my lspci
```
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:02:07.0 VGA compatible controller: nVidia Corporation: Unknown device 0326 (rev a1)
0000:02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
0000:02:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)

```
if that helps anyone...

---

### Post by AutumnForever on 2006-01-09
It's probably been handled already or I'm probably way off, but maybe check your bios. I know when I was having problems with my SB, Emu10k1 I think it is.. was being conflicted by my onboard sound. So maybe try disabling the onboard sound in your bios setup. just an idea..

---

### Post by starfleetcaptainrob on 2006-01-09
Ok, I feel kind of dumb.  It was just the speakers.  I'm not sure why I didn't try that first.  I came home and borrowed the speakers off of my fiancee's computer and plugged them in and got sound.  Sheesh.  So much for my nice 5.1 system.

Thanks to all that replied!

---

